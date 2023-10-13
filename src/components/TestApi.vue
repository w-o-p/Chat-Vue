<template>
    <div>
        <div><b>Команды</b></div>
        <div v-if="isLoad">Данные идут, но пока еще не дошли</div>
        <div v-else>
            <div style="margin-top: 10px;">
                <b>{{ teamData[0].id }}.</b> {{ teamData[0].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[1].id }}.</b> {{ teamData[1].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[2].id }}.</b> {{ teamData[2].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[3].id }}.</b> {{ teamData[3].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[4].id }}.</b> {{ teamData[4].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[5].id }}.</b> {{ teamData[5].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[6].id }}.</b> {{ teamData[6].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[7].id }}.</b> {{ teamData[7].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[8].id }}.</b> {{ teamData[8].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[9].id }}.</b> {{ teamData[9].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[10].id }}.</b> {{ teamData[10].full_name }}
            </div>
            <div style="margin-top: 10px;">
                <b>{{ teamData[11].id }}.</b> {{ teamData[11].full_name }}
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'TestApi',
    data(){
        return {
            teamData: [],
            isLoad: true
        }
    },
    mounted(){
        const url = 'https://free-nba.p.rapidapi.com/teams?page=0';
        const options = {
            method: 'GET',
            headers: {
                'X-RapidAPI-Key': 'b528f179abmshc94e00f6b9e87f5p129814jsn42bb7ca58dff',
                'X-RapidAPI-Host': 'free-nba.p.rapidapi.com'
            }
        };

        fetch(url, options)
        .then((res) => res.json())
        .then((res) => {
            console.log(res.data)
            this.teamData = res.data
            this.isLoad = false
        });
    }
}
</script>
