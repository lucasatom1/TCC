<template>
  <v-container>
    <FormHeaderNew
      boxColor="rgb(176, 161, 198)"
      textLeft1="INICIAL"
      textLeft2="2 DE 2"
      textRight1="FORMULÁRIO 2"
      textRight2="CLIENTE"
      textMiddle1="AVALIAÇÃO DE TECNOLOGIA ASSISTIVA- PREDISPOSIÇÃO AO USO"
      textMiddle2="ATD PA- Br"
      textMiddle3="Para Comparar Dispositivo e Obter Resultados Desejados"
    />

    <FormInfo
      boxColor="rgb(205, 192, 218)"
      name="Nome"
      age="Idade"
      shortGoals="Objetivos a curto prazo da T.A (6 meses)"
      date="Data de Avaliação"
      longGoals="Objetivos a longo prazo da T.A (1 ano +)"
      appraiser="Avaliador"
    />

    <h3>Instruções:</h3>
    <span>
      Escreva o nome de cada dispositivo que você está considerando no espaço
      abaixo de “Dispositivo”. Observe o exemplo dado. Classifique cada
      dispositivo de TA considerando os 12 (A-L)de acordo com a escala abaixo,
      depois circule os 3 itens (A-L) que quais importam para você. Escreva a
      classificação nos espaços apropriados.</span
    >
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <p>5 = O tempo todo (100% do tempo)</p>
        <p>4 = Frequentemente (aproximadamente 75% do tempo)</p>
        <p>3 = Metade do tempo, neutro( aproximadamente 50% do tempo)</p>
      </v-col>
      <v-col cols="12" sm="6" md="3">
        <p>2 = Ás vezes (aproximadamente 25% do tempo)</p>
        <p>1 = Nunca (0% do tempo)</p>
        <p>0 = Não se aplica.</p>
      </v-col>
    </v-row>

    <v-row class="align-center pa-n10">
      <v-col cols="12" sm="6" md="1">
        <p></p>
      </v-col>

      <v-col cols="12" sm="6" md="4 ">
        <p>Questão</p>
      </v-col>

      <v-col cols="12" sm="6" md="1">
        <p>Exemplo: Bengala de 4 apoios</p>
      </v-col>

      <v-col cols="12" sm="6" md="2">
        <p>Dispositivo 1</p>
        <v-text-field placeholder="(nome do dispositivo)"></v-text-field>
      </v-col>

      <v-col cols="12" sm="6" md="2">
        <p>Dispositivo 2</p>
        <v-text-field placeholder="(nome do dispositivo)"></v-text-field>
      </v-col>

      <v-col cols="12" sm="6" md="2">
        <p>Dispositivo 3</p>
        <v-text-field placeholder="(nome do dispositivo)"></v-text-field>
      </v-col>
    </v-row>

    <div v-for="(question, index) in questions" :key="question.id">
      <question-type-3
        @device1="handleQuestionDevice1"
        @device2="handleQuestionDevice2"
        @device3="handleQuestionDevice3"
        :id="question.id"
        :text="question.text"
        :exampleNumber="question.exampleNumber"
        :color="index % 2 == 0 ? 'rgb(229, 223, 237)' : ''"
        :finalComment="
          questions.length - 1 === index
            ? 'Revise cada pontuação total acima. Dispositivo com a pontuação mais alta é o mais elegível ( número máximo de pontos = 60). Entretanto, quando a pontuação total dos dispositivos for próxima, deverá ser dado maior peso a soma dos três itens marcados como mais importantes.'
            : ''
        "
        :finalInfo="questions.length - 1 === index ? true : false"
        :sumDevice1="questions.length - 1 === index ? sumDevice1 : null"
        :sumDevice2="questions.length - 1 === index ? sumDevice2 : null"
        :sumDevice3="questions.length - 1 === index ? sumDevice3 : null"

      />
      <!-- <question-type-3 finalComment="Revise cada pontuação total acima. Dispositivo com a pontuação mais alta é o mais elegível ( número máximo de pontos = 60). Entretanto, quando a pontuação total dos dispositivos for próxima, deverá ser dado maior peso a soma dos três itens marcados como mais importantes."/> -->
    </div>

    <h3>Comentários e Anotações:</h3>
    <br />
    <v-container fluid>
      <v-textarea
        label="Escreva aqui os comentários e anotações"
        auto-grow
        outlined
        rows="3"
        row-height="25"
      ></v-textarea>
    </v-container>
  </v-container>
</template>

<script>
import FormHeaderNew from "../components/FormHeaderNew";
import FormInfo from "../components/FormInfo";
import QuestionType3 from "../components/QuestionType3";

export default {
  components: {
    FormHeaderNew,
    FormInfo,
    QuestionType3,
  },
  name: "Form2",
  data() {
    return {
      sumDevice1: 0,
      sumDevice2: 0,
      sumDevice3: 0,
      questions: [
        {
          id: "A",
          text:
            "Este dispositivo de TA me ajudará a alcançar meus objetivos (incluindo os objetivos primário da TA escritos acima)",
          exampleNumber: "5",
          value: [0, 0, 0],
        },
        {
          id: "B",
          text:
            "Este dispositivo me beneficiará e melhorará minha qualidade de vida ",
          exampleNumber: "3",
          value: [0, 0, 0],
        },
        {
          id: "C",
          text:
            "Eu estou confiante que eu sei como usar este dispositivo e suas variações",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "D",
          text:
            "Eu me sentirei mais seguro ( em segurança, seguro de mim mesmo) usando este dispositivo de TA",
          exampleNumber: "5",
          value: [0, 0, 0],
        },
        {
          id: "E",
          text: "Este dispositivo se encaixará bem à minha rotina diária.",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "F",
          text:
            "Eu tenho capacidade e vigor para usar este dispositivo sem desconforto, estresse ou fadiga",
          exampleNumber: "3",
          value: [0, 0, 0],
        },
        {
          id: "G",
          text:
            "Há suporte, assistência e acomodações para o uso bem sucedido deste dispositivo",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "H",
          text:
            "Este dispositivo se encaixará fisicamente em todos os ambientes desejados (carro, sala de estar etc…)",
          exampleNumber: "3",
          value: [0, 0, 0],
        },
        {
          id: "I",
          text:
            "Eu vou me sentir confortável (não vou ficar constrangido) usando este dispositivo perto dos meus amigos ",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "J",
          text:
            "Eu vou me sentir confortável (não vou ficar constrangido) usando este dispositivo perto dos meus familiares ",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "K",
          text:
            "Eu me sentirei confortável (não vou ficar constrangido) usando este  positivo na escola ou no trabalho",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "L",
          text:
            "Eu me sentirei confortável(e não vou me sentir constrangido ) usando este dispositivo na minha comunidade )",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
      ],
    };
  },
  methods: {
    handleQuestionDevice1(question) {
      this.questions.find(({ id }) => id === question.id).value[0] =
        question.value;

      //atualiza valor pra passar pro obj filho
      this.sumDevice1 = this.questions
        .reduce(function (accumulator, item) {
          return accumulator + item.value[0];
        }, 0);
    },
    handleQuestionDevice2(question) {
      this.questions.find(({ id }) => id === question.id).value[1] =
        question.value;

      //atualiza valor pra passar pro obj filho
      this.sumDevice2 = this.questions
        .reduce(function (accumulator, item) {
          return accumulator + item.value[1];
        }, 0);
    },
    handleQuestionDevice3(question) {
      this.questions.find(({ id }) => id === question.id).value[2] =
        question.value;

      //atualiza valor pra passar pro obj filho
      this.sumDevice3 = this.questions
        .reduce(function (accumulator, item) {
          return accumulator + item.value[2];
        }, 0);
    },
  },
  computed: {
  }
};
</script>

<style lang="scss" scoped>
.mediumPurple {
  background-color: rgb(205, 192, 218);
}
</style>