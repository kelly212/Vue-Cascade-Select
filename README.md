# Vue-Cascade-Select
 Um componente de formulário para selecionar um valor de uma lista de opções.
O componente é compatível com Vuetify 3.x.
## Install 
#### NPM 
Para usar o componente em seu projeto Vue 3, instale o pacote via NPM:

```bash 
npm install v-cascade-select
``` 
## Uso
No seu projeto Vue, importe e registre o componente:

```javascript 
import { createApp } from 'vue';
import App from './App.vue';
import vuetify from './plugins/vuetify';  // if you are already using Vuetify 
import VCascadeSelect from 'v-cascade-select';

const app = createApp(App);

app.use(vuetify);
app.component('VCascadeSelect', VCascadeSelect);
app.mount('#app');
```
## Exemplo de Uso
Você pode usar o componente da seguinte maneira:

```vue

<template>
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
</template>

<script>
import { defineComponent } from 'vue';

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
      { abreviacao: 'SE', descricao: 'Suécia' }
    ]
  }),
  mounted() {
  
  }
});
</script>

```
#### Props
* name (String): Define o nome do campo para envio de formulários.
* id (String): Identificador único para o campo.
* label (String): Texto a ser exibido como rótulo do campo.
* class (String): Classe CSS para estilização. No exemplo, inp inp_upper define o estilo.
* (Boolean): Controla o estado de carregamento. Se true, exibe um indicador de carregamento.
* @update (Event): Evento emitido quando o valor selecionado muda. O valor atualizado é passado para a função definida.
* (Array): Lista de itens que podem ser selecionados. Cada item deve ser um objeto contendo ao menos um título e um valor.
* (Any): O valor atual selecionado.
* item-title (String): O nome da propriedade usada para exibir o título dos itens no dropdown.
* item-value (String): O nome da propriedade usada para definir o valor dos itens.

#### Events
* @update: Disparado sempre que o valor selecionado for atualizado. O valor retornado é o objeto correspondente ao item selecionado, com base nas propriedades item-title e item-value.

#### Slots
Este componente atualmente não utiliza slots.

#### Referências
* https://primevue.org/cascadeselect/ (based on primevue)
