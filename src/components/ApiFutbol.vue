
<template>
    <div id="apiFutbol" class="container py-5">
        <h3>{{title}}</h3>
        <table id="tabla" class="table table-responsive">
            <thead class="thead-dark">
                <tr>
                    <td colspan="4">
                        <input id="buscar" type="text" class="form-control" placeholder="Escriba algo para filtrar" />
                    </td>
                </tr>
                <tr>
                    <th>Date/Status</th>
                    <th>Opponent/Home Team</th>
                    <th>Opponent/Away Team</th>
                    <th>Score</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="matche in matchess" :key="matche.id">
                    <td>{{matche.utcDate}}</td>
                    <td>{{matche.homeTeam.name}}</td>
                    <td>{{matche.awayTeam.name}}</td>
                    <td>{{matche.score.fullTime.home}} - {{matche.score.fullTime.away}}</td>
                </tr>
            </tbody>
            
        </table>
    </div>
</template>
<script>
import axios from 'axios'

export default {
    name: "apiFutbol",

    data () {
        return {
            matchess: [],
            title: "Partidos de Futbol Europeos"
        }
    },
     mounted () {
        fetch('http://127.0.0.1:8000/api/getMatches')
        .then(response => response.json())
        .then(resp => {
            console.log (resp);
            this.matchess = resp.data
        });
    },

};
</script>
