<script>
export default {
  data: () => {
    return {
      typeValue: '',
      typeStatus: false,
      typeArray: ['Обуви', 'Худи', 'Зимней одежды'],
      typingSpeed: 200,
      erasingSpeed: 100,
      newTextDelay: 2000,
      typeArrayIndex: 0,
      charIndex: 0
    }
  },
  methods: {
    typeText() {
      if (this.charIndex < this.typeArray[this.typeArrayIndex].length) {
        if (!this.typeStatus) this.typeStatus = true

        this.typeValue += this.typeArray[this.typeArrayIndex].charAt(this.charIndex)
        this.charIndex += 1

        setTimeout(this.typeText, this.typingSpeed)
      } else {
        this.typeStatus = false
        setTimeout(this.eraseText, this.newTextDelay)
      }
    },
    eraseText() {
      if (this.charIndex > 0) {
        if (!this.typeStatus) this.typeStatus = true

        this.typeValue = this.typeArray[this.typeArrayIndex].substring(0, this.charIndex - 1)
        this.charIndex -= 1
        setTimeout(this.eraseText, this.erasingSpeed)
      } else {
        this.typeStatus = false
        this.typeArrayIndex += 1
        if (this.typeArrayIndex >= this.typeArray.length) this.typeArrayIndex = 0

        setTimeout(this.typeText, this.typingSpeed + 1000)
      }
    }
  },
  created() {
    setTimeout(this.typeText, this.newTextDelay + 200)
  }
}
</script>

<template>
    <div>
        <div class="bg-[url('/cbox.png')] h-96 bg-cover flex items-center relative">
            <div class="m-auto absolute bottom-10 w-full">
                <h1 class="text-5xl mt-4 font-bold text-center text-slate-800">
                  Идеальный магазин для покупки
                  <span id="typed-text shadow-md">{{ typeValue }}</span>
                  <span class="cursor shadow-xl" :class="{ typing: typeStatus }">&nbsp;</span>
                </h1>
            </div>
        </div>
    </div>
</template>

<style scoped>
span.cursor {
    display: inline-block;
    margin-left: 3px;
    width: 4px;
    background-color: black;
    animation: cursorBlink 1s infinite;
}

span.cursor.typing {
    animation: none;
}

@keyframes cursorBlink {
    49% { background-color: black; }
    50%{ background-color: transparent; } 
    99% { background-color: transparent; }
}

</style>