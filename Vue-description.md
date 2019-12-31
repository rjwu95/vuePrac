computed: 단순계산 함수로 어떤 값을 return해서 사용하고 싶을 때 사용 caching된다.

```javascript
computed: {
    // a computed getter
    reversedMessage: function () {
      // `this` points to the vm instance
      return this.message.split('').reverse().join('')
    }
  }
```

method: computed와 비슷하지만 값이 변할 때마다 re-render 시켜준다. caching안된다.

```javascript
methods: {
  now: function () {
    return Date.now()
  }
}
```

watch: asynchronous 처리를 할 때 유용하게 사용하는 method

```javascript
watch: {
    // whenever question changes, this function will run
    question: function (newQuestion, oldQuestion) {
      this.answer = 'Waiting for you to stop typing...'
      this.debouncedGetAnswer()
    }
  },
      created: function () {
    this.debouncedGetAnswer = _.debounce(this.getAnswer, 500)
  },
  methods: {
    getAnswer: function () {
      if (this.question.indexOf('?') === -1) {
        this.answer = 'Questions usually contain a question mark. ;-)'
        return
      }
      this.answer = 'Thinking...'
      var vm = this
      axios.get('https://yesno.wtf/api')
        .then(function (response) {
          vm.answer = _.capitalize(response.data.answer)
        })
        .catch(function (error) {
          vm.answer = 'Error! Could not reach the API. ' + error
        })
    }
```

class and style: 

```javascript
data: {
    obj: { className: true },
   	activeClass: 'active',
    errorClass: 'text-danger'
}
<div v-bind:class="obj"></div> 
// will render 
<div class="className"></div>

<div v-bind:class="[activeClass, errorClass]"></div>
// will render 
<div class="active text-danger"></div>
```

v-if vs v-show

v-show는 style만 바꾸는 것이기 때문에 바꿀때 cost가 많이 들지 않는다. 반면 v-if는 component자체를 변환하는 것이기 때문에 cost많이 든다. **따라서 조건에 따라 계속 변화시켜야 하면 v-show를 쓰고 자주 변하지 않으면 v-if를 써라**

- **v-if와 v-for를 같이쓰지마라** (v-for가 v-if보다 우선순위를 갖고 있다.)

