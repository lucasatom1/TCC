<template>
  <v-container>
    <FormHeaderNew
      boxColor="rgb(117, 147, 62)"
      textLeft1="FOLLOW-UP"
      textLeft2="3 DE 3"
      textRight1="FORMULÁRIO 7"
      textRight2="DISPOSITIVO"
      textMiddle1="AVALIAÇÃO DE TECNOLOGIA ASSISTIVA- PREDISPOSIÇÃO AO USO"
      textMiddle2="ATD PA- Br"
      textMiddle3="FORMULÁRIO DO CLIENTE"
    />
    <h3 class="text-center">Razões Para Não Usar um ou mais Dispositivos</h3>

    <FormInfo
      boxColor="rgb(213, 228, 188)"
      name="Nome"
      age="Idade"
      shortGoals="Objetivos a curto prazo da T.A (6 meses)"
      date="Data de Avaliação"
      longGoals="Objetivos a longo prazo da T.A (1 ano +)"
      appraiser="Avaliador"
    />

    <h3>Instruções:</h3>
    <span>
     Escreva o nome de cada dispositivo que você está considerando no espaço abaixo de “Dispositivo”. 
     Observe o exemplo dado. Classifique cada dispositivo de TA considerando os 12 (A-L)de acordo com a escala abaixo
     , depois circule os 3 itens (A-L) que quais importam para você. Escreva a classificação nos espaços apropriados.
</span
    >
    <v-row>
      <v-col cols="12" sm="6" md="5">
        <p>5 = O tempo todo (100% do tempo)</p>
        <p>4 = Frequentemente (aproximadamente 75% do tempo)</p>
        <p>3 = Metade do tempo, neutro (aproximadamente 50% do tempo)</p>
      </v-col>
      <v-col cols="12" sm="6" md="5">
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
        :finalInfo="false"
        :sumDevice1="questions.length - 1 === index ? sumDevice1 : null"
        :sumDevice2="questions.length - 1 === index ? sumDevice2 : null"
        :sumDevice3="questions.length - 1 === index ? sumDevice3 : null"

      />
    </div>
      <!-- <question-type-3 finalComment="Revise cada pontuação total acima. Dispositivo com a pontuação mais alta é o mais elegível ( número máximo de pontos = 60). Entretanto, quando a pontuação total dos dispositivos for próxima, deverá ser dado maior peso a soma dos três itens marcados como mais importantes."/> -->

    <h3>Instruções:</h3>
    <span>
     Na linha M escreva a letra que representa, dentre as razões abaixo, aquela que levou você a parar de usar o dispositivo.
    </span
    >
    <v-row>
      <v-col cols="12" sm="6" md="4">
        <p>a. Quebrou e eu não consegui usar.</p>
        <p>b. Era inconveniente demais para usar.</p>
        <p>c. Não era do tamanho certo para mim.</p>
        <p>d. Não me ajudou quanto eu esperava.</p>
        <p>e. Era complicado demais para usar.</p>
        <p>f. É muito caro para eu usar.</p>

      </v-col>
      <v-col cols="12" sm="6" md="7">
        <p>g. Eu me senti constrangido usando-o.</p>
        <p>h. Eu não tive o treinamento que eu precisava para usá-lo bem.</p>
        <p>i. Não se encaixava às minhas necessidades/preferências/estilo de vida.</p>
        <div class="d-flex d-inline align-center">
            <span class="mr-5">j. Eu substituí por um recurso ou apoio diferente. Qual ?</span> <v-text-field placeholder=""></v-text-field>
        </div>
        <div class="d-flex d-inline align-center">
            <span class="mr-5">k. Eu não preciso mais dele porque</span> <v-text-field placeholder=""></v-text-field>
        </div>
        <div class="d-flex d-inline align-center">
            <span class="mr-5">l. Outra razão:</span> <v-text-field placeholder=""></v-text-field>
        </div>
        

      </v-col>
    </v-row>

    <p>REVISE AS PONTUAÇÕES ACIMA. Em geral, quanto mais alta a pontuação total( pontuação máxima = 60), 
        mais satisfeito o usuário e mais útil o dispositivo. Entretanto, quando múltiplos dispositivos estão sendo comparados e o 
        número total de pontos de cada um é próximo, mais peso deve ser dado aos três itens circulados como sendo mais importantes.</p>

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
  name: "Form6",
  data() {
    return {
      sumDevice1: 0,
      sumDevice2: 0,
      sumDevice3: 0,
      questions: [
        {
          id: "",
          text:
            "Número de semanas que você usou o recurso",
          exampleNumber: "36",
          value: [0, 0, 0],
        },
        {
          id: "A",
          text:
            "O dispositivo de TA ajudou você a alcançar os seus objetivos (incluindo os objetivos a curto prazo da TA descritos acima)",
          exampleNumber: "5",
          value: [0, 0, 0],
        },
        {
          id: "B",
          text:
            "Este dispositivo me beneficiou você e melhorou sua qualidade de vida",
          exampleNumber: "3",
          value: [0, 0, 0],
        },
        {
          id: "C",
          text:
            "Você está confiante que você obteve o máximo  do dispositivo e de seus componentes?",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "D",
          text:
            "Você se sentiu mais seguro ( certo de você mesmo) usando este dispositivo ?",
          exampleNumber: "5",
          value: [0, 0, 0],
        },
        {
          id: "E",
          text: "Este dispositivo se encaixou à sua rotina?",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "F",
          text:
            "Você teve as habilidades e energia para usar este dispositivo sem desconforto, estresse ou fadiga?",
          exampleNumber: "3",
          value: [0, 0, 0],
        },
        {
          id: "G",
          text:
            "Você teve suporte, assistência e acomodações para usar o dispositivo com sucesso?",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "H",
          text:
            "Este dispositivo se encaixou fisicamente em todos os ambientes desejados (carro, sala de estar etc…)",
          exampleNumber: "3",
          value: [0, 0, 0],
        },
        {
          id: "I",
          text:
            "Você se sentiu confortável (não se sentiu constrangido) usando este dispositivo perto dos meus familiares?",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "J",
          text:
            "Você se sentiu confortável (não se sentiu constrangido)  usando este dispositivo perto dos meus amigos?",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "K",
          text:
            "Você se sentiu confortável (não se sentiu constrangido)  usando este dispositivo na escola ou no trabalho?",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "L",
          text:
            "Você se sentiu confortável (não se sentiu constrangido)  usando este dispositivo na minha comunidade )?",
          exampleNumber: "4",
          value: [0, 0, 0],
        },
        {
          id: "M",
          text:
            "Principal razão pela qual você parou de usar o dispositivo ",
          exampleNumber: "D",
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