# react-basic

![img.png](image/img.png)

- `react` : 페이스북의 UI를 더 잘 만들기 위해 페이스북에서 만든 자바스크립트 UI 라이브러리

- `사용자 정의 태그`를 만들어주는 여러가지 기술이 있는데 리액트 역시도 그런 기술 중에 하나이다.
- 리액트에서 `사용자 정의 태그` 를 `Component` 라고 부른다.

`Component 기능` : 가독성, 재사용성, 유지보수

### npm
- `npm` : Node.js라는 기술을 이용해서 만들어진 여러 앱을 명령어 환경에서 아주 손쉽게 설치할 수 있게 도와주는 도구 즉, Node.js계의 앱스토어, 구글 플레이 같은 역할을 하는 소프트웨어.

### npx
`npx` : 프로그램을 임시로 설치해서 딱 한 번만 실행시키고 지운다고 생각.
- 컴퓨터 공간을 낭비하지 않는다.
- 설치를 실행할 때마다 새로 다운로드하기 때문에 항상 최신 상태이다 .

### JSX
`JSX`는 자바스크립트의 확장 문법. XML과 매우 비슷하게 생겼으며, 이런 형식으로 작성한 코드는 브라우저에서 실행되기 전에 코드가 번들링되는 과정에서 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환된다.

### Props
`Props` : Html 태그 속성(attribute) 같은 것. react에서는 props라 부름. 
- 속성값을 나타내는 키워드.

### State
`State` : Props에 값에 따라서 내부에 구현에 필요한 데이터들. 컴포넌트 내부적으로 사용되는 것들.

`Props`를 사용했는데도 `State`를 사용하는 이유는, 사용하는 쪽과 구현하는 쪽을 철저하게 분리시켜서 양쪽의 편의성을 각자 도모하는 것에 있다.

데이터를 수정하는 로직이나 사용자가 입력한 변경된 데이터를 저장해야 하는 경우, 읽기전용인 Properties(props)에서 변경 데이터 저장은 불가능.
이에 모든 컴포넌트는 state를 가지고 있으며, state에서는 변경된 데이터를 관리할 수 있다. 사용자와 컴포넌트 또는 컴포넌트와 컴포넌트 사이에 상호작용을 하며 값을 바꿀 수 있다.

**_외부에서 알 필요가 없는 정보를 철저하게 은닉하는 것, 철저하게 숨기는 것이 좋은 사용성을 만드는 핵심._** _(굳이 비유를 하자면 전선이 삐져나온 핸드폰이 사용성이 좋을 거라는 생각은 안든다.)_

![img.png](image/props_state.png)

_**사용자 입장에서 알아야 할 것만 알면 된다.**_


### State and Component

- React에서 관리하는 모든 데이터는 부모컴포넌트 -> 자식컴포넌트 이동
- 부모, 자식 컴포넌트는 서로 state에 영향을 끼치지 않는다.
- 각 컴포넌트는 인스턴스화 될 때 각기 독립적으로 관리가 된다.

State는 생성자 호출 시 초기화 시킬 수 있고, setState() 메소드를 통해 변경할 수 있다.

```js
import './App.css';
import TOC from './components/TOC';
import Subject from './components/Subject';
import Content from './components/Content';
import { Component } from 'react';

class App extends Component {
  constructor(props){
    super(props);
    this.state = {  // App이 내부적으로 사용할 상태는 state를 사용한다.
      mode:'read',
      subject:{title:"WEB", sub:"World wide web!"},
      welcome:{title:'Welcome', desc:'Hello, React!'}
    }
  }
  render() {
    return (
      <div className="App">
        <Subject 
          title={this.state.subject.title}
          sub={this.state.subject.sub}
          onChangePage={function(){
            this.setState({mode:'welcome'})
          }.bind(this)}>
        </Subject>
      </div>
    )
  }
}
// State를 쓰는 것은 파일의 뚜껑을 열고 데이터가 바뀌엇다고 로직을 바꾸는 것을 하지않게 해준다.
export default App;
```

```js
import { Component } from 'react';

class Subject extends Component {

    render() {
      return (
        <header>
            <h1><a href="/" onClick={function(e){
                e.preventDefault();
                this.props.onChangePage();
            }.bind(this)}>{this.props.title}</a></h1>
            {this.props.sub}
        </header>  
      );
    }
  }

export default Subject;
```
### State 활용

컴포넌트 내 props, state로 데이터 관리.

state에서 관리하면 좋은 데이터의 종류
- 사용자가 입력한 데이터(textbox, form field)
- 현재 또는 선택된 아이템(현재 탭, 테이블 내 선택된 행)
- 서버로 부터 받는 데이터(객체 리스트)
- 동적인 상태(모델을 열기 및 닫기, 사이드바 열기 및 닫기)