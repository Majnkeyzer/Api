<!--suppress ALL -->
<template>

    <div class="container">
        <div class="uitleg" align="center">
            <h5>Over het gebruik van deze pagina:</h5>
            <p> Aan de linkerzijde van het scherm kunt u de informatie over nieuwe films toevoegen. Voer voor een nieuwe film
                de titel in en een samenvatting. als de film op meerdere tijden speel kun je na het invoeren van elke tijd, volgende
                indrukken om nog een tijd toe te voegen. Dit geldt ook voor zaalnummers. als u alle informatie heeft ingevoerd kunt
                u op opslaan drukken om alle informatie te bewaren.<br><br> Aan de rechter zijde van het scherm kunt u een film
                kiezen uit alle bestaande films, en vervolgens informatie over deze film aanpassen of de hele film, en alle informatie
                hierover verwijderen. Kies een bestande tijd, die verschijnt nadat u een film kiest om deze te verwijderen als u op
                opslaan drukt. Voer een tijd in het tekstvak in om deze toe te voegen als u op opslaan drukt </p>
        </div>
        <div class="row">
            <div class="pull-left">
                <h1>Film Toevoegen</h1>
                <div class="form-group">
                    <label>Titel:</label>
                    <input class="form-control" type="text" v-model="film.titel">
                </div>

                <div class="form-group">
                    <label>Samenvatting:</label>
                    <textarea class="form-control" rows="5" id="comment" v-model="film.samenvatting"></textarea>
                </div>

                <div class="form-group">
                    <label>Speel tijden:</label>
                    <select class="form-control" id="sel1" v-model="film.tijd"> <br>
                        <option>10:00 uur</option>
                        <option>13:00 uur</option>
                        <option>18:00 uur</option>
                        <option>20:00 uur</option>
                    </select>

                </div>

                <button class="button.btn.btn-primary pull-right" @click="submit">Opslaan</button>


                <!--<button class="button.btn.btn-primary" @click="fetchData">Get data</button>-->
                <!--<br><br>-->
                <!--<ul class="list-group">-->
                    <!--<li class="list-group-item" v-for="f in films"> {{ f.titel}} -{{ f.tijd }} -{{ f.samenvatting }}</li>-->
                <!--</ul>-->

            </div>

        </div>
       </div>

</template>

<script>
    export default {
        data() {
            return {
                film: {
                    titel: '',
                    samenvatting: '',
                    tijd: ''
                },
                films: []

            };
        },
        methods: {
            submit() {
                this.$http.post('https://vuesjs.firebaseio.com/data.json', this.film)
                    .then(response => {
                        console.log(response);
                    }, error => {
                        console.log(error);
                    });
            },
            // fetchData() {
            //      this.$http.get('https://vuesjs.firebaseio.com/data.json')
            //            .then(response => {
            //                return response.json();
            //            })
            //            .then(data => {
            //                const resultArray = [];
            //                for (let key in data) {
            //                    resultArray.push(data[key]);
            //                }
            //                this.users = resultArray;
            //            });
            //
            //
            //     }
        },

    }
</script>

<!--<style>-->

<!--</style>-->
