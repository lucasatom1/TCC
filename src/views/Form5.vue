<template>
  <v-container class="grey lighten-5" fluid>
    <FormHeaderNew
      boxColor="rgb(117, 147, 62)"
      textLeft1="FOLLOW-UP"
      textLeft2="1 DE 3"
      textRight1="FORMULÁRIO 5"
      textRight2="CLIENTE"
      textMiddle1="AVALIAÇÃO DE TECNOLOGIA ASSISTIVA- PREDISPOSIÇÃO AO USO"
      textMiddle2="ATD PA- Br"
      textMiddle3="FORMULÁRIO DO CLIENTE"
    />

    <FormInfo
      boxColor="rgb(213, 228, 188)"
      name="Nome"
      age="Idade"
      shortGoals="Objetivos a curto prazo da T.A (6 meses)"
      date="Data de Avaliação"
      longGoals="Objetivos a longo prazo da T.A (1 ano +)"
      appraiser="Avaliador"
    />

    <!-- questao a -->
    <QuestionHeader
      text="Que nota você daria hoje para as suas habilidades nas 9 áreas listadas abaixo, considerando o uso do seu dispositivo de TA atual ou outro auxílio."
      id="A"
      :infos="[
        'Para os itens 1-9 marque a resposta mais adequada(1 para ruim e até 5 para excelente).',
        'Na coluna Nome do Dispositivo escreva o nome da TA que faz uso e onde é relevante (por exemplo “óculos de grau” na primeira linha, “visão”).',
        'Escreva um sinal de mais (+) no espaço onde você espera precisar de mais dispositivos de TA ao longo do próximo ano (por exemplo: “óculos” recebe um mais (+) se você espera precisar de lentes mais fortes durante o próximo ano). Escreva um sinal de menos (-) nos espaços onde você espera diminuir o suporte, e (0) onde você espera que o seu dispositivo de TA deveria continuar o mesmo ao longo do próximo ano.',
      ]"
    />

    <div v-for="(question, index) in questionsA" :key="question.number">
      <question-type-1
        :color="index % 2 == 0 ? 'rgb(213, 228, 188)' : ''"
        :number="question.number"
        :text="question.text"
        :info="
          index === 0
            ? {
                scale1: 'Ruim',
                scale2: 'Médio',
                scale3: 'Excelente',
                input1: 'Nome do  Dispositivo ',
                input2:
                  'Necessita mais (+), menos (-), Permanecer da mesma forma (0)',
              }
            : {}
        "
      />
    </div>
    <!-- questao a -->

    <!-- questao b -->
    <QuestionHeader
      text="Quanto você está satisfeito, atualmente, com as seguintes
        áreas?"
      id="B"
      :infos="[
        'Para os itens 10-21 marque a reposta mais adequada (dê 1 para não satisfeito e até 5 para muito satisfeito).',
      ]"
      text2="Quais são os 3 itens mais importantes para você? Considerando as três áreas mais importantes para você, marque em ordem de prioridade 1º, 2º e 3º os itens mais importantes (1º = mais importante). Deixe as outras linhas em branco."
      text3="Para os 3 itens mais importantes para você, escreva no espaço ao lado, os principais obstáculos e barreiras que você enfrenta."
    />

    <div v-for="(question, index) in questionsB" :key="question.number">
      <question-type-1
        :number="question.number"
        :text="question.text"
        :color="index % 2 == 0 ? 'rgb(213, 228, 188)' : ''"
        :info="
          index === 0
            ? {
                scale1: 'Não Satisfeito',
                scale2: 'Satisfeito',
                scale3: 'Muito Satisfeito',
                input1: '3 mais importantes',
                input2: 'Obstáculos / barreiras',
              }
            : {}
        "
      />
    </div>
    <!-- questao b -->

    <!-- questao c -->
    <QuestionHeader
      text="Por favor, marque todas afirmativas abaixo que descrevam você"
      id="C"
      :infos="[
        'Marque somente aquelas que frequentemente ou geralmente se aplicam a você e ignore aquelas que muito raramente ou nunca se aplicam a você.',
      ]"
    />
    <v-container>
      <v-row>
        <v-col
          v-for="question in questionsC"
          :key="question.number"
          cols="12"
          md="4"
          xs="12"
        >
          <question-type-2 :number="question.number" :text="question.text" />
        </v-col>
      </v-row>

      <!-- questao c -->

      <!-- questao d -->
      <br />
      <h3>Comentários</h3>
      <br />
      <v-textarea
        label="Escreva aqui os comentários"
        auto-grow
        outlined
        rows="3"
        row-height="25"
      ></v-textarea>
      <!-- questao d -->
    </v-container>
  </v-container>
</template>

<script>
import FormHeaderNew from "../components/FormHeaderNew";
import FormInfo from "../components/FormInfo";
import QuestionType1 from "../components/QuestionType1";
import QuestionType2 from "../components/QuestionType2";
import QuestionHeader from "../components/QuestionHeader";

export default {
  components: {
    FormHeaderNew,
    FormInfo,
    QuestionType1,
    QuestionType2,
    QuestionHeader,
  },
  name: "Form5",
  data() {
    return {
      questionsA: [
        {
          number: 1,
          text: "Visão",
        },
        {
          number: 2,
          text: "Audição ",
        },
        {
          number: 3,
          text: "Linguagem",
        },
        {
          number: 4,
          text: "Compreensão, Memória",
        },
        {
          number: 5,
          text: "Física(força, resistência, vigor, disposição)",
        },
        {
          number: 6,
          text: "Uso da parte inferior do corpo(quadril, pernas, pés)",
        },
        {
          number: 7,
          text: "Preensão e uso dos dedos",
        },
        {
          number: 8,
          text: "Uso da parte superior do corpo (braços, ombros e tronco)",
        },
        {
          number: 9,
          text: "Mobilidade (chegar de um lugar ao outro)",
        },
      ],
      questionsB: [
        {
          number: 10,
          text: "Cuidado pessoal e atividade domésticas",
        },
        {
          number: 11,
          text: "Conforto físico e bem-estar/satisfação",
        },
        {
          number: 12,
          text: "Saúde em geral",
        },
        {
          number: 13,
          text: "Liberdade de ir onde deseja",
        },
        {
          number: 14,
          text: " Participação em atividades desejadas",
        },
        {
          number: 15,
          text: "Sucesso/ satisfação educacional",
        },
        {
          number: 16,
          text: "Condição profissional/Potencial",
        },
        {
          number: 17,
          text: "Relações familiares",
        },
        {
          number: 18,
          text: "Relacionamentos próximos, íntimos",
        },
        {
          number: 19,
          text: "Autonomia e autodeterminação(escolha)",
        },
        {
          number: 20,
          text: "Fazer parte, pertencer, sentir-se conectado",
        },
        {
          number: 21,
          text: "Bem estar emocional",
        },
      ],
      questionsC: [
        {
          number: 22,
          text: "Eu tenho o apoio que eu quero da minha família.",
        },
        {
          number: 23,
          text: "Eu faço o que meu terapeuta diz sem questionar.",
        },
        {
          number: 24,
          text: "Eu me sinto encorajado pelos terapeutas e cuidadores.",
        },
        {
          number: 25,
          text: "Eu não tenho certeza de quem eu sou agora.",
        },
        {
          number: 26,
          text: " Eu desejo ir à escola ou trabalhar.",
        },
        {
          number: 27,
          text: "Eu estou frequentemente desanimado.",
        },
        {
          number: 28,
          text: "Eu tenho o apoio que eu quero dos meus amigos.",
        },
        {
          number: 29,
          text: "Eu fico frustado ou me sinto sobrecarregado com frequência.",
        },
        {
          number: 30,
          text: "Eu sinto que, em geral, as pessoas me aceitam.",
        },
        {
          number: 31,
          text: "Eu sou curioso e animado com coisas novas.",
        },
        {
          number: 32,
          text: "Eu estou determinado a atingir meu objetivos.",
        },
        {
          number: 33,
          text: " Eu geralmente sou calmo e paciente.",
        },
        {
          number: 34,
          text: "Eu fico frequentemente com raiva.",
        },
        {
          number: 35,
          text: "Eu sou autodisciplinado.",
        },
        {
          number: 36,
          text: "Eu estou frequentemente deprimido.",
        },
        {
          number: 37,
          text: "Minha vida tem propósito e significado.",
        },
        {
          number: 38,
          text: "Eu preferiria estar sozinho.",
        },
        {
          number: 39,
          text: "Eu quero mais independência.",
        },
        {
          number: 40,
          text: " Meu terapeuta (s) sabe melhor do que eu preciso.",
        },
        {
          number: 41,
          text: "Eu gosto de ter desafios.",
        },
        {
          number: 42,
          text: "Eu sou responsável e confiável.",
        },
        {
          number: 43,
          text: "Eu geralmente estou satisfeito com minha vida.",
        },
        {
          number: 44,
          text: "Eu acho que a tecnologia é interessante.",
        },
        {
          number: 45,
          text: "Eu prefiro viver um estilo de vida mais tranquilo.",
        },
        {
          number: 46,
          text: "Eu sou cooperativo.",
        },
        {
          number: 47,
          text: "Eu frequentemente me sinto isolado e sozinho.",
        },
        {
          number: 48,
          text: "Eu cumpro o que me proponho fazer.",
        },
        {
          number: 49,
          text: "Eu frequentemente me sinto inseguro.",
        },
        {
          number: 50,
          text: "Eu tenho capacidade para resolver situações.",
        },
        {
          number: 51,
          text: "Eu me sinto como se  eu tivesse pouca privacidade.",
        },
        {
          number: 52,
          text: "Eu tenho uma boa imagem de mim mesmo.",
        },
        {
          number: 53,
          text: " Eu vejo meu(s) terapeuta(s) como amigo(s) também.",
        },
        {
          number: 54,
          text: "Eu tenho muita coisas que eu quero realizar.",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.mediumPurple {
  background-color: rgb(205, 192, 218);
}
</style>