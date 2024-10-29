<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
			<v-select :id="id"
													hide-details
													:label="label"
													:class="classe"
													autocomplete="of"
													:density="density"
													:loading="loading"
													:variant="variant"
													:readonly="readonly"
													:disabled="disabled"
													v-model="selectedAux"
													clear-icon="mdi-close"
													:items="filteredItems"
													:clearable="clearable"
													:item-title="itemTitle"
													:item-value="itemValue"
													:return-object="returnObject"
													:menu-props="{closeOnContentClick: false}">
						<template v-slot:prepend-item>
									<div style="padding: 0px 10px;">
												<v-text-field data-lpignore="true" class="inp_search" density="compact" v-model="search" label="Pesquisar" hide-details
																										clear-icon="mdi-close" clearable prepend-inner-icon="mdi-magnify"
																										:placeholder="placeholder" single-line></v-text-field>
									</div>
						</template>
						<template v-slot:item="{ item, props: { onClick } }">
									<v-list-item class="small-list-item" :title="item.title" @click="onClick"/>
						</template>
			</v-select>
</template>

<script>

   export default {
      props: {
         lista: {default: []},
         label: {default: 'Label'},
         placeholder: {default: 'Pesquisar'},
         id: {default: 'select'},
         itemTitle: {default: 'title'},
         classe: {default: ''},
         variant: {default: 'outlined'},
         density: {default: 'compact'},
         model: {default: null},
         itemValue: {default: null},
         loading: {default: true},
         clearable: {default: true},
         returnObject: {default: true},
         disabled: {default: false},
         readonly: {default: false},
      },
      data() {
         return {
            search: '',
            listaAux: [],
         }
      },
      methods: {
         validarCampo(campo) {
            if (campo !== undefined && campo !== null && campo !== '') {
               return true
            } else {
               return false
            }
         },
      },
      mounted() {
 
      },
      computed: {
         filteredItems() {
            if (this.listaAux.length > 0) {
               return this.listaAux
            } else {
               // return this.validarCampo(this.search) ? [] : _.slice(this.lista, 0, 60)
               return this.validarCampo(this.search) ? [] : this.lista.slice(0, 60);
            }
         },
         selectedAux: {
            get() {
               return this.model
            },
            set(v) {
               this.$emit('update', v)
               return this.selectedAux
            }
         },
      },
      watch: {
         search: function () {
            let exp = new RegExp(this.search.trim(), 'i');

            if (this.validarCampo(this.itemTitle)) {
               this.listaAux = this.lista
                .filter(p => exp.test(p[this.itemTitle]))
                .slice(0, 60);
            } else {
               this.listaAux = this.lista
                .filter(p => exp.test(p))
                .slice(0, 60);
            }

         },
      },
   }
</script>
<style lang="scss">
			.inp_search {
						.v-label {
									font-size: 13px !important;
						}
						
						.v-field__field {
									height: 32px;
						}
						
						.v-field__input {
									font-size: 13px !important;
									min-height: 20px !important;
						}
			}
			.small-list-item{
						font-size: 10px!important;
						min-height: 30px !important;
			}

</style>
