# meex

### description

**state management tool to realize the communication between components.**

### core concepts

- State

- Getters

- Mutations

- Actions

- Subscribe

### install

```javascript

npm install meex

yarn add meex

```

### usage method

```javascript

import { Store } from 'meex'

const state = {
  firstState: 1,
  secondState: [],
  thirdState: {}
}

const getters = {
  getState1: (state) => {
    return state.firstState
  },
  getState2: (state) => (arr) => {
    return state.secondState.concat(arr)
  },
  getState3: (state) => (obj) => {
    return state.id = obj.id
  } 
}

const mutations = {
  incrementState1: (state) => {
    state.firstState++
  },
  mergeState2: (state, payload) => {
    state.secondState = state.secondState.concat(payload.arr)
  }
}

const actions = {
  actionState1 ({ commit }) {
    setTimeout(() => {
      commit('incrementState1')
    }, 1000)
  }
}

const store = new Store({
  state,
  mutations,
  getters,
  actions
})

store.commit('incrementState1')
store.commit('mergeState2', {
  arr: [1,2,3]
})

store.dispatch('actionState1')

store.substribe(()=> {
  let firstState = store.getters.getState1
})

```

### notice

If you know vuex and redux, it may help you to be familiar with meex.


