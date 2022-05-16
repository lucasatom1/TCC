<template>
  <v-container class="grey lighten-5" fluid>
    <FormHeaderNew
      boxColor="rgb(176, 161, 198)"
      textLeft1="INICIAL"
      textLeft2="1 DE 2"
      textRight1="FORMULÁRIO 1"
      textRight2="CLIENTE"
      textMiddle1="AVALIAÇÃO DE TECNOLOGIA ASSISTIVA- PREDISPOSIÇÃO AO USO"
      textMiddle2="ATD PA- Br"
      textMiddle3="FORMULÁRIO DO CLIENTE"
    />

    <FormInfo
      boxColor="rgb(205, 192, 218)"
      name="Nome"
      age="Avaliador"
      shortGoals="Dispositivo"
      date="Data de Avaliação"
    />

    <!-- questao a -->
    <QuestionHeader
      text="INCENTIVOS E IMPEDIMENTOS Individuais e Psicossociais ao uso do dispositivo de T.A."
      id="A"
      text2="Leia cada um dos itens abaixo e decida quais são incentivos ou impedimentos ao uso deste dispositivo de tecnologia assistiva por esta pessoa. Então marque um “X” no espaço apropriado. Para aqueles que são neutros, não se aplicam ou não existam a situação apropriada, coloque um “X” no espaço do meio."
    />

    <!-- questao a -->

    <div v-for="(question, index) in questions" :key="question.id">
      <question-type-4
        @scale="handleRadios"
        :id="question.id"
        :text="question.text"
        :color="index % 2 == 0 ? 'rgb(229, 223, 237)' : ''"
        :infos="
          index === 0
            ? {
                scale1: 'Maior Impedimento',
                scale2: 'Impedimento Moderado',
                scale3: 'Menor Impedimento',
                scale4: 'Neutro/ Não se aplica ',
                scale5: 'Menor Incentivo ',
                scale6: 'Incentivo Moderado',
                scale7: 'Maior Incentivo',
              }
            : {}
        "
        :radioSum="questions.length - 1 === index ? radiosSum : null"
      />
    </div>
  </v-container>
</template>

<script>
import FormHeaderNew from "../components/FormHeaderNew";
import FormInfo from "../components/FormInfo";
import QuestionHeader from "../components/QuestionHeader";
import QuestionType4 from "../components/QuestionType4";

export default {
  components: {
    FormHeaderNew,
    FormInfo,
    QuestionHeader,
    QuestionType4,
  },
  name: "Form1",
  data() {
    return {
      radiosSum: null,
      radios: [],
      questions: [
        {
          id: "1",
          text: "Grau no qual a deficiência está incorporada à autoimagem",
          value: null,
        },
        {
          id: "2",
          text: "Visão de barreiras/ Limitações",
          value: null,
        },
        {
          id: "3",
          text: "Experiências de vida em geral",
          value: null,
        },
        {
          id: "4",
          text: "Percepção do controle sobre a qualidade de vida",
          value: null,
        },
        {
          id: "5",
          text: "Expectativa de si mesmo",
          value: null,
        },
        {
          id: "6",
          text: "Grau de participação social",
          value: null,
        },
        {
          id: "7",
          text: "Socialização e habilidade socia",
          value: null,
        },
        {
          id: "8",
          text: "Expectativas da família",
          value: null,
        },
        {
          id: "9",
          text: "Expectativas dos amigos",
          value: null,
        },
        {
          id: "10",
          text: "Desejo de ir à escola / ao trabalho",
          value: null,
        },
        {
          id: "11",
          text: "Cooperação com os terapeutas e plano de reabilitação",
          value: null,
        },
        {
          id: "12",
          text: "Interesse em novas coisas",
          value: null,
        },
        {
          id: "13",
          text: "Visão de oportunidades",
          value: null,
        },
        {
          id: "14",
          text: "Atitude/ Visão sobre a vida",
          value: null,
        },
        {
          id: "15",
          text: "Humor(Personalidade) e Emoção",
          value: null,
        },
        {
          id: "16",
          text: "Grau de autodisciplina e paciência",
          value: null,
        },
        {
          id: "17",
          text: "Desejo de usar tecnologia(s)",
          value: null,
        },
        {
          id: "18",
          text: "Desejo por independência",
          value: null,
        },
        {
          id: "19",
          text: "Autoestima",
          value: null,
        },
        {
          id: "20",
          text: "Habilidade de enfrentamento",
          value: null,
        },
        {
          id: "21",
          text: "Experiência prévia com o uso de tecnologia geral",
          value: null,
        },
        {
          id: "22",
          text: "Grau de expressividade",
          value: null,
        },
      ],
    };
  },
  methods: {
    handleRadios(radio) {
      this.radios[radio.id] = radio.value;
      this.mountSumRadiosObject();
    },
    mountSumRadiosObject(radio) {
      this.radiosSum = this.radios.reduce(function (obj, num) {
        // Get the integer value of the number
        var int = Math.floor(num);

        // If the integer doesn't already exist as a key in the object, create it
        if (!obj.hasOwnProperty(int)) {
          obj[int] = [];
        }

        // Push the number to its integer key
        obj[int].push(num);

        // Pass the object on to the next loop
        return obj;
      }, {});
      console.log(this.radiosSum);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>