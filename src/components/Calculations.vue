<template>
  <!-- <div class="number">
    <input type="text" v-model.lazy="objectNumber">
    <br>
    <input type="text" v-model="num1"> *
    <input type="text" v-model="num2"> *
    <input type="text" v-model="num3">
  </div>
  <div class="colors">
    <div class="color" id="color"></div>
    <div class="color reference-color" id="color"></div>
  </div> -->
  <div class="colors-array">
    <p>Тестовые цвета</p>
    <div
      v-for="num in testColors"
      :key="num"
      :style="{backgroundColor: `rgb(${getColorFromNumber(num, testColors).r},${getColorFromNumber(num, testColors).g},${getColorFromNumber(num, testColors).b})`}"
      class="color"
      id="number-to-color"
    ></div>
  </div>
  <div class="colors-array">
    <p>Boat</p>
    <div
      v-for="num in boat"
      :key="num"
      :style="{backgroundColor: `rgb(${getColorFromNumber(num, boat).r},${getColorFromNumber(num, boat).g},${getColorFromNumber(num, boat).b})`}"
      class="color"
      id="number-to-color"
    ></div>
  </div>
  <div class="colors-array">
    <p>House 2</p>
    <div
      v-for="num in house2"
      :key="num"
      :style="{backgroundColor: `rgb(${getColorFromNumber(num, house2).r},${getColorFromNumber(num, house2).g},${getColorFromNumber(num, house2).b})`}"
      class="color"
      id="number-to-color"
    ></div>
  </div>
  <div class="colors-array">
    <p>House 5</p>
    <div
      v-for="num in house5"
      :key="num"
      :style="{backgroundColor: `rgb(${getColorFromNumber(num, house5).r},${getColorFromNumber(num, house5).g},${getColorFromNumber(num, house5).b})`}"
      class="color"
      id="number-to-color"
    ></div>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue'

const objectNumber = ref(0)
// const num1 = ref(256)
// const num2 = ref(256)
// const num3 = ref(256)

// const objectNumber = computed(() => {
//   return num1.value * num2.value * num3.value
// })

const testColors = [16711680, 65280, 255]

const boat = [ 0, 335544320, 352321536, 369098752, 385875968, 402653184, 419430400, 436207616, 16777216, 452984832, 486539264, 469762048, 503316480, 520093696, 33554432, 50331648, 536870912, 570425344, 67108864, 553648128, 587202560, 83886080, 620756992, 603979776, 100663296, 117440512, 637534208, 134217728, 671088640, 654311424, 150994944, 687865856, 704643072, 167772160, 184549376, 721420288, 738197504, 788529152, 218103808, 754974720, 201326592, 805306368, 771751936, 822083584, 234881024, 838860800, 855638016, 872415232, 251658240, 889192448, 268435456, 905969664, 922746880, 939524096, 956301312, 285212672, 301989888, 973078528, 989855744, 1006632960, 1023410176, 1040187392, 1073741824, 1056964608, 1090519040, 1124073472, 1107296256, 1140850688, 1157627904, 1174405120, 1191182336, 1224736768, 1207959552, 1241513984, 1258291200, 1275068416, 1291845632, 1308622848, 1325400064, 318767104, 1342177280, 1358954496, 1392508928, 1375731712, 1409286144, 1426063360, 1459617792, 1442840576, 1476395008 ]
const house2 = [ 33554432, 16777216, 0 ]
const house5 = [ 167772160, 671088640, 1006632960, 335544320, 838860800, 0 ]

watch(objectNumber, (objectNumber) => {
  // const maxNumber = float(objectNumberMax);
  // float minNumber = float(objectNumberMin); // Удалить!!!
  // const whiteColorNumber = pow(255.0, 3.0);
  // float valueOfDivision = whiteColorNumber / float(objectNumbersAmount);

  // float num = objectNumber * (whiteColorNumber - 2.0 * valueOfDivision) / maxNumber;

  const num = objectNumber;

  // // Получается только красный цвет:
  // const r = objectNumber / 65536;
  // const g = (objectNumber % 65536) / 256;
  // const b = (objectNumber % 65536) % 256;

  const r = Math.floor(objectNumber / 65536);
  const g = Math.floor((objectNumber % 65536) / 256);
  const b = (objectNumber % 65536) % 256;

  // const r = num / 256 / 256 % 255;
  // const g = num / 256 % 255;
  // const b = num % 255;

  const el = document.getElementById('color');
  el.style.backgroundColor = `rgb(${r},${g},${b})`;

  console.log('r g b', r, g, b);
})

// function getColor(objectNumber, arr) {
//   // // Algorithm 1
//   // const r = Math.floor(num / 65536);
//   // const g = Math.floor((num % 65536) / 256);
//   // const b = (num % 65536) % 256;

//   // Algorithm 3
//   const whiteColorNumber = 256 ** 3;
//   const valueOfDivision = whiteColorNumber / arr.length;
//   const num = objectNumber * (whiteColorNumber - valueOfDivision) / findMax(arr);
//   const r = num / 256 / 256 % 255;
//   const g = num / 256 % 255;
//   const b = num % 255;

//   return { r, g, b }
// }

function getColorFromNumber(objectNumber, arr) {

  // // Algorithm 1 (монохромно при двух цветах, 5 цветов - красные, много цветов - нормально)
  // const num = objectNumber / arr.length
  // const r = Math.floor(num / 65536);
  // const g = Math.floor((num % 65536) / 256);
  // const b = (num % 65536) % 256;

  // // Algorithm 2 (монохромно при двух цветах, остальные - нормально)
  // const whiteColorNumber = 256 ** 3;
  // const valueOfDivision = whiteColorNumber / arr.length;
  // const num = objectNumber * (whiteColorNumber - valueOfDivision) / findMax(arr);
  // const r = Math.floor(num / 65536);
  // const g = Math.floor((num % 65536) / 256);
  // const b = (num % 65536) % 256;

  // Algorithm 3 (рабочий !!!)
  const whiteColorNumber = 256 ** 3;
  const valueOfDivision = whiteColorNumber / arr.length;
  const num = objectNumber * (whiteColorNumber - valueOfDivision) / findMax(arr);
  const r = num / 256 / 256 % 255;
  const g = num / 256 % 255;
  const b = num % 255;

  return { r, g, b }
}

function findMax(arr) {
  let max = 0;
  arr.forEach(el => {
    if (el > max) max = el
  });
  return max
}


// ///////////////////////////////////////////

// // Рабочий вариант № 3:

// float maxNumber = float(objectNumberMax);
// // float minNumber = float(objectNumberMin); // Удалить!!!
// float whiteColorNumber = pow(255.0, 3.0);
// float valueOfDivision = whiteColorNumber / float(objectNumbersAmount);

// float num = objectNumber * (whiteColorNumber - 2.0 * valueOfDivision) / maxNumber;

// float r = mod(num / 255.0 / 255.0, 255.0);
// float g = mod(num / 255.0, 255.0);
// float b = mod(num, 255.0);

// return vec3(r, g, b) / 255.0;

// ///////////////////////////////////////////
</script>

<style scoped>
.color {
  display: inline-block;
  width: 50px;
  height: 50px;
  border: 1px solid black;
}
.reference-color {
  background-color: rgb(255, 255, 255);
}
</style>
