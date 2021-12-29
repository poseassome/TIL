# MovieApp만들기(2)
작성일시: 2021년 12월 30일 오전 1:41

## Router

router를 설치하여 페이지 이동을 가능하게 한다.

```jsx
npm i react-router-dom@5.3.0
```

```jsx
import {
  BrowserRouter as Router,
  Switch,
  Route,
} from "react-router-dom";
import Home from "./routes/Home";
import Detail from "./routes/Detail";

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/hello">
          <h1>hello</h1>
        </Route>
        <Route path="/movie/:id">
          <Detail />
        </Route>
        <Route path="/">
          <Home />
        </Route>
      </Switch>
    </Router>
  )
}

export default App;
```

`<Switch>`는 route을 찾는 역할,<br/>
`<Route>`는 url에서 [localhost/다음부분](http://localhost/다음부분) 의미함.<br/>
`<Route>`안에 유저가 있는 url에 따라 보여주고 싶은 컴포넌트를 작성한다.

BrowerRouter는 일반적인 홈페이지 경로이며,<br/>
HashRouter는 앞에 /#/이 붙는다.

`<Switch>`를 사용하는 이유는 한 번에 하나의 <Route>만 렌더링하기 위해서이다.<br/>
(react는 두 개의 route도 한 번에 렌더링 하는 것이 가능하다.)

`path=”/”` 는 홈 화면으로 간다는 의미이다.<br/>
해당 route는 가장 마지막에 작성해야 한다.<br/>
(Route는 path의 앞부분부터 일치하는 부분이 있으면 거기서 OK하고 다음으로 넘어가지 않는다.)

## Link

현 route에서 다른 route로 이동하기 위해,
컴포넌트.js에서 <Link />를 사용한다.<br/>
⇒ 브라우저 새로고침 없이 유저를 다른 페이지로 이동시켜준다.

(`<a>`를 사용하면 페이지 전체가 재로딩 된다.)

```jsx
import PropTypes from "prop-types";
import { Link } from "react-router-dom";

function Movie({ id, coverImg, title, summary, genres }) {
  return (
    <div>
      <img src={coverImg} alt={title} />
      <h2><Link to={`/movie/${id}`}>{title}</Link></h2>
      <p>{summary}</p>
      <ul>
        {genres.map((g) => (
          <li key={g}>{g}</li>
        ))}
      </ul>
    </div>
  )
}

Movie.propTypes = {
  coverImg: PropTypes.string.isRequired,
  summary: PropTypes.string.isRequired,
  title: PropTypes.string.isRequired,
  genres: PropTypes.arrayOf(PropTypes.string).isRequired
}

export default Movie;
```

여기서 API의 movie의 id를 전달 받아서 페이지 이동시 id값으로 정보를 불러오고자 한다.

현재 `<Movie />`는 `<Home />`으로 부터 필요한 인자들을 전달받고있으므로 Home.js에서 id값을 추가하고 Movie.js에서도 그 변수명을 추가한다.

```jsx
import { useEffect, useState } from "react";
import Movie from "../components/Movie";

function Home() {
  const [loading, setLoading] = useState(true);
  const [movies, setMovies] = useState([]);

  const getMovies = async () => {
    const json = await (
      await fetch(
        `https://yts.mx/api/v2/list_movies/json?minimum_rating=8.5&sort_by=year`
      )
    ).json();
    setMovies(json.data.movies);
    setLoading(false);
  }
  useEffect(() => {
    getMovies();
  }, []);

  return (
    <div>{loading ? (
      <h1>Loading...</h1>
    ) : (
      <div>
        {movies.map((movie) =>
          <Movie
            key={movie.id}
            id={movie.id}
            coverImg={movie.medium_cover_image}
            title={movie.title}
            summary={movie.summary}
            genres={movie.genres} />)}
      </div>
    )}
    </div>
  )
};

export default Home;
```

## useParams( )

이 함수를 사용하면 react router는 바로 이 변수의 값을 넘겨준다.

현재 Movie.js를 보면 영화제목을 클릭하면 Detail.js로 이동하고, id값을 같이 넘겨준다.<br/>
Detail.js에서 `/:id` 로 변수명을 설정하였고,
`const {id} =useParams();` 로 변수의 값을 밥아서 fetch하는 url에 작성해준다. (꼭 중괄호 안에 작성한다.)

```jsx
import { useEffect } from "react";
import { useParams } from "react-router-dom";

function Detail() {
  const { id } = useParams();
  const getMovie = async () => {
    const json = await (
      await fetch(`https://yts.mx/api/v2/movie_details.json?movie_id=${id}`)
    ).json();
  }
  useEffect(() => {
    getMovie();
  }, []);
  return <h1>Detail</h1>;
}

export default Detail;
```

이제 CSS를 적용하면 완성이다.

---