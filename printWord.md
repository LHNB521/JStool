<!--  该函数是模拟打印机打印字  -->
 // 打印字
 const printWord = (word: string, time = 200) => {
    return new Promise<void>(resolve => {
      setTimeout(() => {
        const a: any = document.getElementById('header')
        a.innerText = word
        resolve()
      }, time)
    })
  }
  // 循环打印
  async function main(str: string[]) {
    // eslint-disable-next-line no-constant-condition
    while (true) {
      // 无限循环
      for (let j = 0; j < str.length; j++) {
        // 写入
        for (let i = 0; i <= str[j].length; i++) {
          // eslint-disable-next-line no-await-in-loop
          await printWord(str[j].substr(0, i)) // 显示当前字符串的前 i 个字符
        }
        // 回退
        // 回退前先等一秒
        // eslint-disable-next-line no-await-in-loop
        await new Promise<void>(resolve => {
          setTimeout(() => {
            resolve() // 等待 1000 毫秒后 Promise 完成
          }, 1000) // 等待 1000 毫秒
        })
        for (let i = str[j].length; i >= 0; i--) {
          // eslint-disable-next-line no-await-in-loop
          await printWord(str[j].substr(0, i), 200) // 显示当前字符串的前 i 个字符，间隔 200 毫秒
        }
      }
    }
  }
  const str = [
    '你问我何时归故里',
    '我也轻声地问自己',
    '不是在此时',
    '不知在何时',
    '我想大约是在冬季'
  ]
  main(str)
