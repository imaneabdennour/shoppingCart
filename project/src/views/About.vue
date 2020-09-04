<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <div class="card w-50 centrer">
      <div class="card-body">
        <h5 class="card-title">Services</h5>
        <ul class="list-unstyled">
          <li
            v-for="service in services"
            :key="service.id"
            class="test"
            @click="
              $set(service, 'selected', !service.selected);
              selected2.includes(service.id)
                ? selected2.splice(selected2.indexOf(service.id), 1) //removes it
                : selected2.push(service.id);
              calculTotal();
            "
          >
            <a href="#" class="noStyle">
              <div
                class="card w-40 card-body unactiveLi"
                :class="{ activeLi: service.selected }"
              >
                {{ service.nom }} <br />
                <span class="price"> {{ service.prix }} {{ devise }} </span>
              </div>
            </a>
          </li>
        </ul>
        <h5 style="font-weight: normal">Total : {{ total }} {{ devise }}</h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  msg: String,
  data() {
    return {
      total: 0,
      selectedId: null,
      selected: undefined,
      selected2: [],
      displayCategory: true,
      devise: "$",
      services: [
        {
          id: 1,
          nom: "Développement WEB",
          prix: 400,
        },
        {
          id: 2,
          nom: "Traduction",
          prix: 200,
        },
        {
          id: 3,
          nom: "Langues",
          prix: 100,
        },
      ],
    };
  },
  methods: {
    select(id) {
      this.selectedId = id;
      this.displayCategory = false;
    },
    calculTotal() {
      this.total = 0;
      for (let i = 0; i < this.services.length; i++) {
        //boucle f selected2 or services ? => boucle sur services
        if (this.selected2.includes(this.services[i].id)) {
          this.total += this.services[i].prix;
        }
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h5 {
  margin-bottom: 20px;
  font-family: "Courier New";
  font-weight: bolder;
  color: whitesmoke;
  font-size: 50px;
}

.centrer {
  margin: auto;
  background: #587e76;
}
.price {
  color: #3e4444;
  margin-top: 10px;
}
.noStyle {
  text-decoration: none;
  color: #e6e2d3;
  font-family: Verdana;
  font-weight: bold;
}
a {
  color: inherit;
}
.test {
  margin: 10px;
}
.activeLi {
  background: #86af49 !important;
}
.unactiveLi {
  background: #eca1a6;
}
</style>
