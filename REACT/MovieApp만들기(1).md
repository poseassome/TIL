# MovieApp만들기(1)
작성일시: 2021년 12월 29일 오전 1:21

# Movie App 만들기

영화 API를 불러와서 영화 목록을 출력한다.

Loading 중에는 내용이 보이지않고 Loading이 끝나면 가져온 정보를 출력한다.

```jsx
import { useEffect, useState } from "react";
import Movie from "./components/Movie";

function App(){
	const [loading, setLoading] = useState(true);
	return (
		<div>
			{loading? (<h1>Loading...</h1>
				) : (
					null
				)
		</div>
	);
};
```

## API가져오기

```jsx
useEffect(() => {
	fetch(
		`https://yts.mx/api/v2/list_movies/json?minimum_rating=8.5&sort_by=year`
	).then((response) => response.json()
	).then((json) => {
		setMovies(json.data.movies);
	  setLoading(false);
	});
}, []);
```

요즘은 **async-await**를 사용해서 불러온다.

```jsx
const getMovies = async () => {
  const response = await fetch(
    `https://yts.mx/api/v2/list_movies/json?minimum_rating=8.5&sort_by=year`
  );
  const json = await response.json();
  setMovies(json.data.movies);
  setLoading(false);
}

useEffect(() => {
	getMovies();
}, [])
```

```jsx
/* 더 간략한 코드 */

const getMovies = async () => {
  const json = await (
    await fetch(
      `https://yts.mx/api/v2/list_movies/json?minimum_rating=8.5&sort_by=year`
    )
  ).json();
  setMovies(json.data.movies);
  setLoading(false);
};

useEffect(() => {
	getMovies();
}, []);
```
<br/>

## 데이터 출력하기

데이터를 출력하기 위해 **map( )** 을 사용한다.

```jsx
const [movies, setMovies] = useState([]);

return (
  <div>{loading ? (
    <h1>Loading...</h1>
  ) : (
    <div>
      {movies.map((movie) => (
        <div key={movie.id}>
          <img src={movie.medium_cover_image} />
          <h2>{movie.title}</h2>
          <p>{movie.summary}</p>
          <ul>
            {movie.genres.map((g) => (
              <li key={g}>{g}</li>
            ))}
          </ul>
        </div>
      ))}
    </div>
  )}
  </div>
)
```

내부에 코드들이 너무 많아서 Movie 컴포넌트를 새로 생성한다.
<Br/>

### Movie.js

```jsx
import PropTypes from "prop-types";

function Movie({ coverImg, title, summary, genres }) {
  return (
    <div>
      <img src={coverImg} alt={title} />
      <h2>{title}</h2>
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

App.js에서 필요한 변수를 받아온다.

### App.js

```jsx
import Movie from "./components/Movie";

return (
  <div>{loading ? (
    <h1>Loading...</h1>
  ) : (
    <div>
      {movies.map((movie) =>
        <Movie
          key={movie.id}
          coverImg={movie.medium_cover_image}
          title={movie.title}
          summary={movie.summary}
          genres={movie.genres} />)}
    </div>
  )}
  </div>
)
```

key는 react에서만 map안에서 component들을 render할 때 사용한다.

<br/>


## router사용

react router는 페이지를 전환하는 것으로,<br/>
현재는 localhost에 있고 → movies/movie.id가 붙은 페이지로 이동하고자한다.

**📁route**폴더를 만들고 그 안에 **Home.js**를 만들어 App.js의 내용을 모두 가져온다.<br/>
App은 아무내용도 보여주지 않고, route를 render해야한다.

### Home.js

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

### App.js

```jsx
function App(){
	return null;
}

export default App;
```

---