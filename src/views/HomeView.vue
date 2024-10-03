<template>
  <div>
    <v-container>
      <br>
      <div style="text-align: center">
        <h1>Vue Cascade Select</h1>
        <br>
      </div>
      <v-row justify="center">
        <v-col cols="6">
         
          <v-cascade-select name="pais"
                            :model="pais"
                            id="pais"
                            label="Selecione"
                            :loading="false"
                            @update="(v)=>{pais=v}"
                            :lista="paises"
                            item-title="descricao"
                            item-value="abreviacao">
          </v-cascade-select>
          Selecionado: {{pais}}
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { defineComponent } from 'vue';

// Components
import VCascadeSelect from '../components/VCascadeSelect.vue';

export default defineComponent({
  name: 'HomeView',
  data:()=>({
    pais: null,
    loading: true,
    paises: [
      { abreviacao: 'BR', descricao: 'Brasil' },
      { abreviacao: 'US', descricao: 'Estados Unidos' },
      { abreviacao: 'CA', descricao: 'Canadá' },
      { abreviacao: 'MX', descricao: 'México' },
      { abreviacao: 'AR', descricao: 'Argentina' },
      { abreviacao: 'JP', descricao: 'Japão' },
      { abreviacao: 'CN', descricao: 'China' },
      { abreviacao: 'DE', descricao: 'Alemanha' },
      { abreviacao: 'FR', descricao: 'França' },
      { abreviacao: 'IN', descricao: 'Índia' },
      { abreviacao: 'IT', descricao: 'Itália' },
      { abreviacao: 'GB', descricao: 'Reino Unido' },
      { abreviacao: 'RU', descricao: 'Rússia' },
      { abreviacao: 'AU', descricao: 'Austrália' },
      { abreviacao: 'ZA', descricao: 'África do Sul' },
      { abreviacao: 'ES', descricao: 'Espanha' },
      { abreviacao: 'PT', descricao: 'Portugal' },
      { abreviacao: 'KR', descricao: 'Coreia do Sul' },
      { abreviacao: 'SA', descricao: 'Arábia Saudita' },
      { abreviacao: 'SE', descricao: 'Suécia' }
    ]
  }),

  components: {
    VCascadeSelect,
  },
  mounted() {
  
  }
});
</script>
