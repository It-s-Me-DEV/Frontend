# 13주차

## 목차

- [1. Next.js](#1-nextjs)
- [2. 프로젝트 진행 상황](#2-프로젝트-진행-상황)


## 1. Next.js

### \<Link> component

React Router도 `<Link>` component를 가지고 있으나 차이점은 Next.js 에서는 조금 더 서버 사이드 렌더링에 최적화되어 있습니다. Next의 링크는 프리페치라고 해서 링크에 마우스를 올리기만 해도 미리 그 링크의 정보들을 다운로드해 로딩 시간을 최소화합니다.

| 특징    | HTML \<a> 태그  | React Router <Link>         | Next.js <Link>                     |
| ----- | ------------ | --------------------------- | ---------------------------------- |
| 기능    | 페이지 이동       | 페이지 이동, 상태 유지, 동적 라우팅       | 페이지 이동, 서버 사이드 렌더링 최적화, 프리페칭       |
| 사용 환경 | 모든 HTML 문서   | React 애플리케이션                | Next.js 애플리케이션                     |
| 동작 방식 | 브라우저 전체 새로고침 | JavaScript를 이용한 페이지 변경      | JavaScript를 이용한 페이지 변경, 서버 사이드 렌더링 |
| 추가 기능 | 없음           | 상태 유지, 동적 라우팅, CSS 클래스 전환 등 | 프리페칭, 이미지 최적화, 서버 사이드 렌더링 최적화      |

이러한 이유로 Next.js에서는 굳이 \<a>를 쓸 필요는 없어보입니다.

## 2. 프로젝트 진행 상황

사이드바에서 재생목록을 구현 중인데, 구현할 부분이 너무 많아 `NowPlaying.tsx`로 분리했습니다.


```
// 노래가 현재 재생 중인지 상태 나타내는 타입
type Playing =
    { 
        type : "playing";
    } 
    | {
        type : "paused";
    } 
    | {
        type : "not playing";
    };

const [ playingState, setplayingState ] = useState<Playing>({ type : "not playing" });

    function togglePlaying() : void {
        if (playingState.type === "playing") {
            setplayingState( { type : "paused" });
        }    
        else if (playingState.type === "paused" || playingState.type === "not playing") {
            setplayingState({ type : "playing" });
        }
    }
```
이렇게 재생 중이면 일시정지 아이콘을, 재생 중이 아니면 재생 아이콘이 뜨게 만들어주었습니다.

```
type nowPlaying = {
    id: number;
    title: string;
    artist: string;
};

const NowPlaying : React.FC = () => {
    const [ isVisible, setisVisible ] = useState<boolean>(true);
    
    function toggleVisible () : void {
        setisVisible(!isVisible);
    }
    
    const nowPlayings: nowPlaying[] = [
        { id: 1, title : "Now Playing", artist : "Artist"},
        { id: 2, title : "Now Playing-----", artist : "Artist"},
        { id: 3, title : "The Less I Know The Better", artist : "Tame Impala"},
    ];

    return (
        <>
            <LibraryHeader>
                    <h3>Now Playing</h3>
                    <button onClick={toggleVisible}>
                        <AiOutlinePlus style={{ transform: isVisible ? 'rotate(45deg)' : 'rotate(0deg)', transition: 'transform 0.3s' }}/>
                    </button>
            </LibraryHeader>
            <NowPlayingList isVisible={isVisible}>
                {nowPlayings.map((nowPlayingItem) => (
                    <NowPlayingEntry key={nowPlayingItem.id} nowPlayingItem={nowPlayingItem} />
                ))}
            </NowPlayingList>
        </>
    )
};
```
재생목록 보기/ 안 보기 기능을 추가했습니다.


```
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 1;
overflow: hidden;
```

이 CSS를 추가함으로써, 글자 수가 너무 많으면 ...으로 보이게 처리하였습니다.

![image](https://github.com/user-attachments/assets/ea772586-f4ef-4f16-9371-9270fa81b246)
![image](https://github.com/user-attachments/assets/28fed45e-c7e6-4cad-a697-e952b1ee8ced)

### 추가 사항

1. 재생 버튼을 다른 화면에서 쓰는 재생 버튼과 호환되게 설정하기\
(Context 등 전역 상태 사용)
2. 재생 버튼을 누르면 다른 재생 중인 노래는 { type : "not playing" }으로 바꾸고 재생 중단되게 만들기
3. 드래그 앤 드롭으로 재생목록 순서 바꾸기
