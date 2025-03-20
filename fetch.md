# Promise

- 비동기 코드에서 콜백 사용시 코드복잡도 향상되어 Promise 클래스 사용

### 예시 (callback패턴으로 비동기 처리 코드)

자바스크립트에서 비동기 코드 (setTimeout, fetch, db요층 등)는 순차적으로 실행되지 않고, 일정시간이 지난후 실행됨.  
비동기 작업이 끝난 후 특정 코드를 실행하려면 콜백 함수 사용  
callback은 함수 매개변수로 전달되는 함수

callback 예시

```javascript
const a = (callback) => {
  setTimeout(() => {
    console.log(1)
    callback()
  }, 1000)
}
const b = () => console.log(2)

a(() => {
  b()
})
```

#### Promise 예시

promise 클래스 사용은 callback이라는 매개변수 대신해서 resolve 개념으로  
실행의 위치를 보장
a함수 호출 후 new 키워드로 promise 생성자 함수 호출
promise 만들어진 instancce는 then메소드로 이어서 작성

```javascript
const a = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(1)
      resolve()
    }, 1000)
  })
}
const b = () => console.log(2)

a().then(() => {
  b()
})
```

```javascript
const a = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(1)
      resolve()
    }, 1000)
  })
}

const b = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(2)
      resolve()
    }, 1000)
  })
}
const c = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(3)
      resolve()
    }, 1000)
  })
}
const d = () => console.log(4)

a()
  .then(b)
  .then(c)
  .then(d)
  .then(() => console.log("done"))
```

### Promise getMovies 예시

```javascript
const getMovies = movieName => {
  return neew Promise(resolve => {
    fetch(`https://wwww.omdbapi.com/?apikey=7035c60c&s=${movieName}`)
      .then(res => res.json())
      .then(res => {
        console.log(res)
        resolve()
      })
  })
}

getMovies('frozen')
  .then(() => {
    console.log('겨울왕국!')
    return getMovies('avengers')
  })
  .then(() => {
    console.log('어벤져스!')
    return getMovies('avatar')
  })
  .then(() => {
    console.log('아바타!')
  })

```

### Async / Await

await 키워드는 async 키워드와 함께 사용

```javascript
const a = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(1)
      resolve()
    }, 1000)
  })
}
const b = () => console.log(2)
// a().then(() => b())

const wrap = async () => {
  await a()
  b()
}
wrap()

// getMovies('frozen')
//   .then(() => {
//     console.log('겨울왕국!')
//     return getMovies('avengers')
//   })
//   .then(() => {
//     console.log('어벤져스!')
//     return getMovies('avatar')
//   })
//   .then(() => {
//     console.log('아바타!')
//   })

const wrap = async () => {
  await getMovies("frozen")
  console.log("겨울왕국!")
  await getMovies("avengers")
  console.log("어벤져스!")
  await getMovies("avatar")
  console.log("아바타!")
}
wrap()
```

### Resolve, Reject 그리고 에러 핸들링

```javascript
const delayed = (index, cb, errorCb) => {
  setTimeout(() => {
    if (index > 10) {
      errorCb(`${index}는 10보다 클 수 없습니다.`)
      return
    }
    console.log(index)
    cb(index + 1)
  }, 1000)
}

delayadd(
  13,
  (res) => console.log(res),
  (err) => console.error(err)
)

// async await로 작성
const delayed = (index) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (index > 10) {
        reject(`${index}는 10보다 클 수 없습니다.`)
        return
      }
      console.log(index)
      resolve(index + 1)
    }, 1000)
  })
}

delayadd(13)
  .then(res => => console.log(res))
  .catch(err => console.error(err))

const wrap = async () => {
  const res = await delayadd(2)
  console.log(res)
}
```

```javascript
const getMovies = (movieName) => {
  return new Promise((resolve) => {
    fetch(`https://www.omdbapi.com/?apikey=7035c60c&s=${movieName}`)
      .then((res) => res.json())
      .then((res) => resolve(res))
  })
}

const titles = ["frozen", "avengers", "avatar"]

// title.forEach(async (title) => {
//   const movies = await getmovies(title)
//   console.log(title, movies)
// })

const wrap = async () => {
  for (const title of titles) {
    const movies = await getMovies(title)
    console.log(title, movies)
  }
}
wrap()
```

# fetch(주소, 옵션)

- 비동기 코드에서 콜백 사용시 코드복잡도 향상되어 Promise 클래스 사용
- 네트워크를 통해 리소스의 요청(Request) 및 응답(Response)을 처리 가능
- Promise 인스턴스를 반환

```javascript
fetch("https://www.omdbapi.com/?apikey=7035c60c&s=avengers")
  .then((res) => res.json())
  .then((json) => console.log(json))
// fetch 함수 사용 시 응답의 결과를 json 메소드를 호출해야지만 응답 데이터 결과 꺼낼 수 있음
// fetch는 promise <response>를 반환
// res.json()json데이터를 바로 반환하는게 아니라 promise<json>형태를 반환
// 그래서 추가해야 작동.then(json => console.log(json))
```

# then -> await async 키워드로 대체

```javascript
fetch("https://www.omdbapi.com/?apikey=7035c60c&s=avengers")
  .then((res) => res.json())
  .then((json) => console.log(json))

const wrap = async () => {
  const res = await fetch("https://www.omdbapi.com/?apikey=7035c60c&s=avengers")
  const json = await res.json()
  console.log(json)
}
wrap()
```

# then 옵션 get

```javascript
fetch("https://www.omdbapi.com/?apikey=7035c60c&s=avengers", {
  method: "GET",
  headers: {
    "Content-Type": "application/json",
  }, // 서버로 전송하는 요청에 대한 정보
  body: JSON.stringify({
    name: "DongHee Lee",
    age: 85,
    email: "41ehdgml@naver.com",
  }), // 요청에 대한 데이터
})
  .then((res) => res.json())
  .then((json) => console.log(json))

const wrap = async () => {
  const res = await fetch("https://www.omdbapi.com/?apikey=7035c60c&s=avengers")
  const json = await res.json()
  console.log(json)
}
wrap()
```
