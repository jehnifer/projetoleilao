<template>
    <div class="container">
        <form @submit.prevent="salvar(), listar(idLeilao)">
            <strong>
                <label >LEILÃO </label>
                <label v-if="idLeilao != null">{{this.idLeilao}} </label> 
                <label >{{this.leilaoItem}} </label>
            </strong>
            <br>
            <label class="label">LANCE MINIMO </label>
            <label class="label" v-if="lanceMinimoParam != null">{{this.lanceMinimoParam}}</label>   
            <br>
            <div class="columns">
                <div class="column">
                    <label class="label">VALOR</label>
                    <input 
                        type="number"
                        class="input"
                        placeholder="Digite o valor"
                        v-model="lance.valor">
                </div>

                <div class="column">
                    <label class="label">PARCIPANTE</label>

                    <div class="select">
                        <select v-model="lance.participante.id">
                            <option v-for="participante in participantes" :key="participante.id" :value="participante.id">{{participante.nome}}</option>
                        </select>
                    </div>
                </div>
            </div>

            <button style="margin-top: 10px" class="button is-primary">
                    Salvar  
            </button>
        </form>

        <table class="table">
            <thead>
                <tr>
                    <th>PARTICIPANTE</th>
                    <th>VALOR</th>
                    <th>AÇÕES</th>
                </tr>
            </thead>

            <tbody>
                <tr v-for="lance of lances" :key="lance.id">
                    <td>{{ lance.participante.nome }}</td>
                    <td>{{ lance.valor }}</td>
                    <td>
                        <button @click="editar(lance), listar(idLeilao)" class="button is-warning">Editar </button>
                        <button @click="remover(lance), listar(idLeilao)" class="button is-danger">Excluir </button>
                    </td>
                </tr>
            </tbody>
        </table>

    </div>
</template>

<script>
import Lance from '@/services/lance'
import Participante from '@/services/participante'

export default {
    data(){
        return{
            lance:{
                id: '',
                valor: '',
                participante: {
                    id: '',
                    nome: ''
                },
                leilao: {
                    id: this.$route.params.id,
                    item: this.$route.params.item,
                    lanceMinimo: this.$route.params.lanceMinimo
                }
            },
            //this.$route.params.id
            lanceMinimoParam: this.$route.params.lanceMinimo,
            idLeilao: this.$route.params.id,
            leilaoItem: this.$route.params.item,
            lances:[],
            participantes:[],
        }
    },
    mounted(){
        this.listar(this.idLeilao);
        this.preencheSelectParticipante();
    },
    methods:{
        listar(idLeilao){
            Lance.listar(idLeilao).then(res => {
                this.lances = res.data;
            });
        },
        salvar(){
            if(!this.lance.id){
                Lance.salvar(this.lance);
                alert('Lance salvo com sucesso!');
                this.lance.valor = '';
            } else {
                Lance.editar(this.lance);
                alert('Editado com sucesso!');
                this.lance.valor = '';
            }
        },
        remover(lance){
            Lance.remover(lance);
            alert('Removido com sucesso!');
        },
        editar(lance){
            this.lance = lance;
        },
        preencheSelectParticipante(){
            Participante.listar().then(res => {
                this.participantes = res.data;
            })
        }
    }
}
</script>

<style>

</style>
