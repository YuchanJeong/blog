---
title: "Javascript"
showDate: false
categories:
  - \summaries
tags:
  - javascript
---

## JS Data

### 1. Type

| Data Type | Details                                                                                                                                                                                                                                                                                                                 |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| string    | - 쌍따음표("")나 따음표('')로 감싸서 표현<br>- Template literals(\`${변수}`)로 변수 사용 가능<br>- +로 합치기 가능(이때 다른 타입은 문자화)<br>- str[n]으로 character 읽기 가능(read only)<br>- String(data), data.toString()으로 문자화 가능<br>\*_Escape Sequence_<br>ㅤ└ \n (new line)<br>ㅤ└ \t (tap)               |
| number    | - Number(str)로 숫자화 가능<br>ㅤ\*_숫자가 아닌 문자열이 있으면 NaN_<br>- parseInt(str)로 정수화 가능, parseFloat(str)으로 숫자화 가능<br>ㅤ\*_숫자가 아닌 문자열이 뒤에 있으면 숫자인 부분까지 숫자화_                                                                                                                 |
| boolean   | true \| false                                                                                                                                                                                                                                                                                                           |
| array     | - 대괄호([])로 감싸서 표현<br>- arr[i]로 element 읽기 가능<br>- arr[i] = value로 arr의 i index에 value 할당 가능<br>- `new Array.from({ length: n })`으로 n개의 undefined를 가진 배열 생성 가능<br>- `new Array(n).fill(element)`로 n개의 element를 가진 배열 생성 가능                                                 |
| object    | - 중괄호({})로 감싸서 표현<br>- odj.key와 obj[str]으로 value 읽기 가능<br>- odj.key = value와 obj[str] = value로 obj의 key에 value (생성)할당 가능<br>- delete obj[str]로 key-value 삭제 가능<br>- `str in obj`로 key 존재 여부 판단 가능<br >\*_Optional Chaining_<br >ㅤ└ obj.key1?.key2는 key1이 있을 때만 key2 확인 |
| null      | 의도적으로 비움                                                                                                                                                                                                                                                                                                         |
| undefined | 값이 할당되지 않음                                                                                                                                                                                                                                                                                                      |

- falsy
  - false, null, undefined, "", 0, NaN (나머지는 truthy)
- [typeof](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/typeof)
  - 평가 전 데이터 타입을 string으로 반환
  - function은 "function"
  - undeclared variable은 "undefined"
  - null과 array는 "object"
    - null은 data === null로 판단
    - array는 Array.isArray(data)로 판단
  - NaN은 isNaN(number)으로 판단

### 2. Properties & Methods

#### 1\) <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String">String</a>

<table>
  <thead>
    <th>Properties & Methods</th>
    <th>Return</th>
  </thead>
  <tbody>
    <tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/length">length</a></td>
      <td>문자열 안의 코드 유닛 수</td>
    </tr>
    <tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf">indexOf</a>(searchValue[, fromIndex])</td>
      <td>searchValue의 첫 번째 등장 인덱스,<br>찾을 수 없으면 -1<br><span style="font-style: italic;">*.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/lastIndexOf">lastIndexOf</a>()는 마지막 등장 인덱스</span></td>
    </tr>
    <tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/includes">includes</a>(searchValue[, fromIndex])</td>
      <td>searchValue를 포함하고 있는지 여부</td>
    </tr>
    <tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/slice">slice</a>(beginIndex[, endIndex])</td>
      <td>추출된 부분(~이상~미만)을 담는 새로운 string</td>
    </tr>
    <tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/split">split</a>([separator[, limit]])</td>
      <td>separator(문자열|정규식)로 끊은 문자열들의 array</td>
    </tr>
    <tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/match">match</a>(<a href="https://github.com/YuchanJeong/_WIL/blob/master/Etc/Regex.md">regexp</a>)</td>
      <td>정규식과 일치하는 문자열을 포함하는 array,<br>찾을 수 없으면 null<br><span style="font-style: italic;">*g옵션이 없을 때 캡처된 그룹 및 정보도 배열에 포함</span></td>
    </tr>
    <tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace">replace</a>(regexp|subStr, newSubStr|function)</td>
      <td>패턴과 처음 일치하는 부분이 교체된 새로운 string<br><span style="font-style: italic;">*.<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replaceAll">replaceAll</a>()은 모든 일치 문자 교체</span></td>
    </tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase">toUpperCase</a>()<br>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase">toLowerCase</a>()</td>
      <td>모두 대문자로 바꾼 string<br>모두 소문자로 바꾼 string</td>
    </tr>
    </tr>
      <td>str.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/trim">trim</a>()</td>
      <td>양끝의 공백을 제거한 string</td>
    </tr>
  </tbody>
</table>

#### 2\) <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number">Number</a> & <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math">Math</a>

<table>
  <thead>
    <th>Properties & Methods</th>
    <th>Return</th>
  </thead>
  <tbody>
    <tr>
      <td>num.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed">toFixed</a>([digits])</td>
      <td>고정 소수점 표기법을 사용하여 나타낸 수의 string<br><span style="font-style: italic;">*digits: 소수점 뒤에 나타날 자릿수, 기본값 0</span></td>
    </tr>
    <tr>
      <td>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/abs">abs</a>(x)</td>
      <td>숫자의 절댓값</td>
    </tr>
    <tr>
      <td>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/max">max</a>([x[, y[, …]]])<br>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/min">min</a>([x[, y[, …]]])</td>
      <td>0개 이상의 인수 중에서 제일 큰 수<br>0개 이상의 인수 중에서 제일 작은 수</td>
    </tr>
    <tr>
      <td>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil">ceil</a>(x)<br>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/floor">floor</a>(x)<br>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/round">round</a>(x)</td>
      <td>인수보다 크거나 같은 수 중에서 가장 작은 정수<br>인수보다 작거나 같은 수 중에서 가장 큰 정수<br>인수에 가장 가까운 정수</td>
    </tr>
    <tr>
      <td>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt">sqrt</a>(x)</td>
      <td>√x</td>
    </tr>
    <tr>
      <td>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/pow">pow</a>(x, n)</td>
      <td>x의 n제곱값</td>
    </tr>
    <tr>
      <td>Math.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/random">random</a>()</td>
      <td>0 이상 1 미만의 부동소수점 의사 난수</td>
    </tr>
  </tbody>
</table>

#### 3\) <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array">Array</a>

<table>
  <thead>
    <th>Properties & Methods</th>
    <th>Return</th>
  </thead>
  <tbody>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/length">length</a></td>
      <td>배열 안의 요소 수<br><span style="font-style: italic;">*arr.length === 0은 빈 배열</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf">indexOf</a>(searchValue[, beginIndex])</td>
      <td>searchValue의 첫 번째 등장 인덱스,<br>찾을 수 없으면 -1<br><span style="font-style: italic;">*.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf">lastIndexOf</a>()는 마지막 등장 인덱스</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes">includes</a>(searchValue[, beginIndex])</td>
      <td>searchValue를 요소로 포함하고 있는지 여부</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice">slice</a>(beginIndex[, endIndex])</td>
      <td>추출된 부분(~이상~미만)을 담는 array</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join">join</a>([separator])</td>
      <td>모든 요소를 separator로 구분지어 연결한 string<br><span style="font-style: italic;">*separator를 생략하면 쉼표(,)로 구분</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/concat">concat</a>([value1[, ...[, valueN]]])</td>
      <td>콜백 배열이나 값들을 기존 배열에 합친 array</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach">forEach</a>(callback(currentValue<br>[, index[, array]])[, thisArg])</td>
      <td>undefined<br><span style="font-style: italic;">*콜백 함수를 각 요소에 대해 실행</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map">map</a>(callback(currentValue<br>[, index[, array]])[, thisArg])</td>
      <td>콜백 함수를 각 요소에 대해 실행한 결과의 array</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter">filter</a>(callback(currentValue<br>[, index[, array]])[, thisArg])</td>
      <td>콜백 함수의 결과가 참인 요소의 array</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/find">find</a>(callback(currentValue<br>[, index[, array]])[, thisArg])</td>
      <td>콜백 함수의 결과가 참인 요소 중 첫 번째 item,<br>찾을 수 없으면 undefined</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex">findIndex</a>(callback(currentValue<br>[, index[, array]])[, thisArg])</td>
      <td>콜백 함수의 결과가 참인 요소 중 첫 번째 요소의 인덱스,<br>찾을 수 없으면 -1</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce">reduce</a>(callback(accValue[, curValue<br>[, curIndex[, array)[, initialValue]]]])</td>
      <td>콜백 함수의 누적 결과 값(last accValue)<br><span style="font-style: italic;">*initialValue는 첫 accValue의 값이며,<br>생략 시 arr[0]이 첫 accValue, arr[1]이 첫 curValue</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort">sort</a>([compareFunction])</td>
      <td>정열된 array(원본)</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse">reverse</a>()</td>
      <td>순서가 반전된 array(원본)</td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice">splice</a>(beginIndex[, deleteCount<br>[, item1[, ...[, itemN]]]])</td>
      <td>제거한 요소를 담은 array<br><span style="font-style: italic;">*배열(원본)의 요소를 교체<br>*deleteCount를 생략하면 배열(원본)의 마지막까지 삭제</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push">push</a>(item1[, ...[, itemN]])</td>
      <td>요소가 추가된 배열의 새로운 length<br><span style="font-style: italic;">*배열(원본)의 끝에 하나 이상의 요소를 추가<br>*.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift">unshift</a>()는 배열(원본)의 앞에 추가</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop">pop</a>(item1[, ...[, itemN]])</td>
      <td>배열의 마지막 item<br><span style="font-style: italic;">*배열(원본)의 마지막 요소 삭제<br>*.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/shift">shift</a>()는 배열(원본)의 첫 번째 요소 삭제</span></td>
    </tr>
    <tr>
      <td>arr.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/flat">flat</a>([depth])</td>
      <td>depth 번 만큼 다차원 배열을 푼 array<br><span style="font-style: italic;">*depth의 기본값은 1</span></td>
    </tr>
  </tbody>
</table>

\*_beginIndex, endIndex의 값이 음수일 때, 끝에서부터의 위치를 의미_
<br>

#### 4\) <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object">Object</a>

<table>
  <thead>
    <th>Properties & Methods</th>
    <th>Return</th>
  </thead>
  <tbody>
    <tr>
      <td>Object.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign">assign</a>(target, ...sources)</td>
      <td>출처 객체들로부터 하나 이상의 속성들이 복사된 목표 object<br><span style="font-style: italic;">*동일한 키를 갖는 속성은 뒤의 출처 값으로 덮어쓰여짐</span></td>
    </tr>
    <tr>
      <td>Object.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/keys">keys</a>(obj)</td>
      <td>모든 속성의 키(문자열)를 반환한 array<br><span style="font-style: italic;">*Object.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/values">values</a>(obj)는 값의 array</span></td>
    </tr>
    <tr>
      <td>Object.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries">fromEntries</a>(arr)</td>
      <td>[key, value] 형태의 다차원 배열을 변환한 object<br><span style="font-style: italic;">*Object.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/entries">entries</a>(obj)는 [key, value] 형태의 이차원 array</span></td>
    </tr>
    <tr>
      <td>Object.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty">hasOwnProperty</a>(key)</td>
      <td>특정 프로퍼티를 가지고 있는지 여부</td>
    </tr>
  </tbody>
</table>

### 3. Etc

**1\) Destructuring Assignment(구조 분해 할당)**

> 배열/객체의 속성을 해체 후 그 값을 개별 변수에 할당하는 표현식

- Array
  ```js
  const arr = [1, 2, 3, 4, 5];
  const [a, , b, ...rest] = arr;
  // a는 1, b는 3, rest는 [4, 5]
  ```
- Object
  ```js
  const obj = { name: "X", age: 10, gender: "male" };
  const { name, gender: sex, address = "Korea" } = obj;
  // name는 "X", sex는 "male", address는 "Korea"
  ```

**2\) Spread Syntax(전개 구문)**

> ...data의 형태로 문자열·배열·객체를 펼치는 표현식

- String
  ```js
  const str = "Che";
  // [...str]는 ["C", "h", "e"]
  // {...str}는 { "0": "C", "1": "h", "2": "e" }
  ```
- Array
  ```js
  const arr1 = [1, 2, 3];
  // [...arr1]은 [1, 2, 3], !== arr1
  // {...arr1}는 { "0": 1, "1": 2, "2": 3 }
  const arr2 = [4, 5, 6];
  // [...arr1, ...arr2]는 [1, 2, 3, 4, 5, 6]
  ```
- Object
  ```js
  const obj = { a: 1, b: 2, c: 3 };
  // {...obj1}은 { "a": 1, "b": 2, "c": 3 }, !== obj1
  const obj2 = { c: 1, d: 2, e: 3 };
  // {...obj1, ...obj2}는 { "a": 1, "b": 2, "c": 1, "d": 2, "e": 3}
  ```
- `Rest Prams`
  ```js
  const func = (team, ...members) => ({ 팀: team, 멤버: members });
  const myTeam = func("KT", "Smeb", "Score", "Ucal", "Deft", "Mata");
  /* 
  myTeam은 {
    팀: "KT",
    멤버: ["Smeb", "Score", "Ucal", "Deft", "Mata"],
  };
  */
  ```

**3\) Immutability(불변성)**

- Primitive Type(원시 타입)
  - string, number, boolean, undefined, null
  - 변수에 값을 저장
  - immutable
- Reference Type(참조형 타입)
  - array, object, function
  - 변수에 heap의 주소를 저장, 값은 heap에 저장
  - 같은 주소(heap)를 참조할 때 하나 변화 시 일괄 변화
  - mutable

**4\) Shallow Copy(얕은 복사) & Deep Copy(깊은 복사)**

- Shallow Copy
  - 복사한 참조형 데이터 내부의 참조형 데이터는 같은 주소 참조
- Deep Copy
  - 복사한 참조형 데이터 내부의 참조형 데이터도 다른 주소 참조

## JS Operator

**1\) Ternary Operator(삼항 연산자)**

- 조건 ? 조건이 true일 때 : 조건이 false일 때

**2\) Logical Operator(논리 연산자)**

<table>
  <thead>
    <th>Operator</th>
    <th>Details</th>
  </thead>
<tbody>
  <tr>
    <td>&&</td>
    <td>- and (모두 truthy일 때 true)<br>- leftExpr && rightExpr<br>ㅤ└ leftExpr이 truthy일 때, rightExpr<br>ㅤ└ leftExpr이 falsy일 때, leftExpr</td>
  </tr>
  <tr>
    <td>||</td>
    <td>- or (하나라도 truthy일 때 true)<br>- leftExpr || rightExpr<br>ㅤ└ leftExpr이 truthy일 때, leftExpr<br>ㅤ└ leftExpr이 falsy일 때, rightExpr</td>
  </tr>
  <tr>
    <td>??</td>
    <td>- leftExpr ?? rightExpr (nullish coalescing(널 병합))<br>ㅤ└ leftExpr이 null 혹은 undefined가 아닐 때, leftExpr <br>ㅤ└ leftExpr이 null 혹은 undefined 때, rightExpr</td>
  </tr>
  <tr>
    <td>!</td>
    <td>- not (falsy일 때 true)</td>
  </tr>
</tbody>
</table>

**3\) Comparison Operator(비교 연산자)**

<table>
  <thead>
    <th>Operator</th>
    <th>Details</th>
  </thead>
<tbody>
  <tr>
    <td>a === b</td>
    <td>값과 타입이 같을 때 true</td>
  </tr>
  <tr>
    <td>a !== b</td>
    <td>값이나 타입이 다를 때 true</td>
  </tr>
  <tr>
    <td>a > b</td>
    <td>a > b일 때 true</td>
  </tr>
  <tr>
    <td>a < b</td>
    <td>a < b일 때 true</td>
  </tr>
  <tr>
    <td>a >= b</td>
    <td>a >= b일 때 true</td>
  </tr>
  <tr>
    <td>a <= b</td>
    <td>a <= b일 때 true</td>
  </tr>
</tbody>
</table>

**4\) Arithmetic Operator(산술 연산자)**

<table>
  <thead>
    <th>Operator</th>
    <th>Details</th>
  </thead>
<tbody>
  <tr>
    <td>a + b</td>
    <td>덧셈</td>
  </tr>
  <tr>
    <td>a - b</td>
    <td>뺄셈</td>
  </tr>
  <tr>
    <td>a * b</td>
    <td>곱셈</td>
  </tr>
  <tr>
    <td>a / b</td>
    <td>나눗셈</td>
  </tr>
  <tr>
    <td>a % b</td>
    <td>나머지</td>
  </tr>
</tbody>
</table>
</details>

**5\) Assignment Operator(할당 연산자)**

<table>
  <thead>
    <th>Operator</th>
    <th>Details</th>
  </thead>
<tbody>
  <tr>
    <td>a += b</td>
    <td>a = a + b</td>
  </tr>
  <tr>
    <td>a -= b</td>
    <td>a = a - b</td>
  </tr>
  <tr>
    <td>a *= b</td>
    <td>a = a * b</td>
  </tr>
  <tr>
    <td>a /= b</td>
    <td>a = a / b</td>
  </tr>
  <tr>
    <td>a %= b</td>
    <td>a = a % b</td>
  </tr>
</tbody>
</table>

**6\) Increment Operator(증감 연산자)**

<table>
  <thead>
    <th>Operator</th>
    <th>Details</th>
  </thead>
<tbody>
  <tr>
    <td>a++/--</td>
    <td>연산 후 1증가/감소</td>
  </tr>
  <tr>
    <td>++/--a</td>
    <td>1증가/감소 후 연산</td>
  </tr>
</tbody>
</table>

## JS Control Statement

**1\) Conditional Statement(조건문)**

- if 조건문
  ```js
  if (조건1) {
    조건1이 truthy일 때
  } else if (조건n) {
    조건n이 truthy일 때
  } else {
    조건이 모두 falsy일 때
  }
  ```
- switch 조건문
  ```js
  switch (대상) {
    case 케이스n: 대상이 케이스n일 때
      break;
    default: 해당 케이스가 없을 때
  }
  ```

**2\) Iterative Statement(반복문)**

- for 반복문

  ```js
  for (초기값; 반복 조건; 증감값) {
    반복내용;
  }

  // for of 배열
  for (let item of iterator) {
    반복내용;
  }

  // for in 객체
  for (let key in object) {
    반복내용;
  }
  ```

- while 반복문

  ```js
  while (반복 조건) { 반복 내용 }
  ```

  | Escape   | Details                                        |
  | -------- | ---------------------------------------------- |
  | break    | 해당 반복문 종료                               |
  | continue | 해당 반복 내용을 종료하고 다음 반복으로 넘어감 |
  | _label_  | 해당 label의 반복문을 대상으로 함              |

  ```js
  outer: for (item of arr) {
    inner: for (el of item) {
      if (el === 0) {
        break outer;
      }
      if (el === 1) {
        continue inner;
      }
    }
  }
  ```

## JS Function

**1\) 함수 작성**

1. Named Function Declaration(기명 함수 선언)

   ```js
   function 함수() {}
   ```

   - 호이스팅 시 `일시적 사각지대`(코드 실행 전까지 초기화가 일어나지 않음)에 빠지지 않음

2. Anonymous Function Expression(익명 함수 표현)

   ```js
   const 변수 = function () {};
   ```

3. Arrow Function(화살표 함수)

   ```js
   const 변수 = () => {};
   ```

   - 인자가 하나일 때, 인자의 소괄호 생략 가능
   - { return } 생략 가능
   - 객체 데이터는 소괄호로 묶어야 함
   - `메서드 함수로 적합하지 않음`
   - `생성자 함수로 사용할 수 없음`

**2\) 고차 함수**

1.  Timer Function(타이머 함수)

    | Type                   | Details                                                |
    | ---------------------- | ------------------------------------------------------ |
    | setImmediate(콜백)     | 즉시 함수 실행<br/>_\*setTimeout(콜백, 0) 사용은 지양_ |
    | setTimeout(콜백, ms)   | 일정 시간 후 함수 실행                                 |
    | setInterval(콜백, ms)  | 일정 시간 마다 함수 실행                               |
    | clearImmediate(타이머) | 해당 Immediate 함수를 종료                             |
    | clearTimeout(타이머)   | 해당 Timeout 함수를 종료                               |
    | clearInterval(타이머)  | 해당 Interval 함수를 종료                              |

2.  Callback Function(콜백 함수)

    - 함수의 「인자」로 사용되는 함수
    - ```js
      function timeout(cb) {
        setTimeout(() => {
          console.log("start");
          // 함수의 실행 위치 보장
          cb();
        }, 1000);
      }

      timeout(() => {
        console.log("done");
      });
      ```

3.  `Closure Function`(클로저 함수)

    - 함수를 return하는 함수
    - 외부 함수의 「변수」를 내부 함수에서 재사용
    - ```js
      const makeCounter = (x) => {
        // 함수 변경 없이 value에 할당 불가능 (캡슐화)
        let value = x;

        // 내부함수 여러개 생성 가능
        return {
          // 스코프 체이닝 (하위 스코프 우선)
          up: (x) => {
            value += x;
            return value;
          },
          down: (y) => {
            value -= y;
            return value;
          },
        };
      };

      // 함수 재활용 가능
      const counter1 = makeCounter(1);
      const counter2 = makeCounter(2);
      counter1.up(7); // -> 8
      counter2.down(7); // -> -5
      counter2.up(7); // -> 2
      // counter1과 counter2의 value는 서로에게 영향 X
      ```

4.  `Curry Function`(커리 함수)

    - 함수를 return하는 함수
    - 외부 함수의 「인자」를 내부 함수에서 재사용
    - ```js
      const greeting = (x) => {
        return (y) => {
          return `${x} ${y}`;
        };
      };

      // 함수 재활용 가능
      const hello = greeting("Hello");
      const goodMorning = greeting("goodMorning");
      hello("guys"); // -> 'Hello guys'
      hello("ladies"); // -> 'Hello ladies'
      goodMorning("guys"); // -> 'goodMorning guys'
      goodMorning("ladies"); // -> 'goodMorning ladies'
      ```

## JS Class

```js
class 클래스 {
  constructor() {}
}

class 하위_클래스 extends 상위_클래스 {
  constructor() {
    super();
  }
}

const 인스턴스 = new 클래스();
```

- `static` : 클래스에서만 참조 및 호출 가능
- `#` : 내부에서만 참조 및 호출 가능

<details>
<summary>example</summary>
<div markdown=1>

```js
/* 1) 클래스 */
class Vehicle {
  //constructor: 클래스의 파라미터
  constructor(name, wheel) {
    this.name = name;
    this.wheel = wheel;
  }

  //static
  static hi = "hi";

  static isVehicle(vehicle) {
    return vehicle instanceof Vehicle;
  }

  //private
  #private = "private";

  #saySecret() {
    console.log(this.#private);
  }

  //property
  bye = "bye";

  //method
  beep() {
    this.#saySecret();
    console.log("beep!");
  }
}

/* 2) 클래스 상속 */
class Car extends Vehicle {
  constructor(name, wheel, year) {
    //super: 상위 클래스의 파라미터
    super(name, wheel);
    this.year = year;
  }

  getWheel() {
    this.beep();
    console.log(`bye: ${this.bye}`);
    console.log(`wheel: ${this.wheel}`);
  }
}

/* 3) prototype */
// 공통 메서드 함수는 생성자의 prototype에 할당해서 메모리 절약 가능
// prototype chain : 해당 객체 -> 생성자 -> 상위 생성자 -> Object
Vehicle.prototype.getInfo = function () {
  console.log(`${this.name}(${this.year})`);
};

/* 4) 클래스로 인스턴스(객체) 생성 */
const myCar = new Car("벤츠", 4, "2016");
const yourCar = new Car("BMW", 4, "2020");

// ========== //

Vehicle.hi; // "hi"
Vehicle.isVehicle(myCar); // true

myCar.bye; // "bye"
myCar.beep; // -> private -> beep!
myCar.getWheel(); // -> private -> beep! -> wheel: 4
myCar.getInfo(); // -> 벤츠(2016)
yourCar.getInfo(); // -> BMW(2020)
```

</div>
</details>

## JS Asynchronous

**1) Promise**

- 실행은 되지었지만 아직 결과를 반환하지 않은 객체
- resolve는 성공값으로 `then`으로 연결
- reject는 실패값으로 `catch`로 연결
- `finally`는 마지막에 무조건 실행
- Promise changing
  - then에서 반환한 값이 다음 then으로 넘어감
  - 반환값이 프로미스면 resolve 후 넘어감
  - 에러는 catch에서 한 번에 처리
- 여러 프로미스 동시 실행
  - `Promise.all([promise, ...])`
    - 하나라도 실패하면 catch로 이동
    - 각 결과는 배열에 담겨서 반환
  - `Promise.allSettled([promise, ...])`
    - 실패가 있어도 catch로 이동하지 않음
    - 각 결과는 status 프로퍼티를 가지고 status가 fulfilled인 경우 value 프로퍼티, rejected인 경우 reason 프로퍼티를 가짐

**2) async/await**

- 프로미스 앞에 await을 붙히면, 해당 프로미스가 resolve될 때까지 기다린 뒤 다음 로직으로 넘어감
- async 함수 내에서만 await 사용 가능
- async 함수는 항상 프로미스 반환
- try/catch로 에러 처리
- `for await (promise of [promise, ...])`으로 반복 가능

## JS Etc

### 1. DOM

> [DOM(문서 객체 모델)](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model)은 메모리에 웹 페이지 문서 구조를 표현함으로써 스크립트 및 프로그래밍 언어와 페이지를 연결함

| Methods                                                                                                                                                                           | Details                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| document.[querySelector](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector)("selector")                                                                        | 문서 내에서 selector와 일치하는 첫 번째 요소                                                                                                                                                                                 |
| document.[querySelectorAll](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelectorAll)("selector")                                                                  | 문서 내에서 selector와 일치하는 NodeList<br>\*_NodeList[i]로 개별 요소 선택_<br>\*_for이나 forEach로 요소들 반복처리_                                                                                                        |
| document.[createElement](https://developer.mozilla.org/ko/docs/Web/API/Document/createElement)("tag")                                                                             | 문서 내에 해당 tag 요소 생성<br>\*_아직 DOM tree에 연결 X_                                                                                                                                                                   |
| .[appendChild](https://developer.mozilla.org/ko/docs/Web/API/Node/appendChild)(aChild)                                                                                            | 대상의 마지막 자식 노드로 붙임<br>\*D*OM tree에 연결*                                                                                                                                                                        |
| .[addEventListener](https://developer.mozilla.org/ko/docs/Web/API/EventTarget/addEventListener)("event", functionRef\*)                                                           | 이벤트 발생 시 함수 호출<br>\*_[event](https://developer.mozilla.org/ko/docs/Web/Events): click\|focus\|blur\|scroll_<br>\*_[event.target](https://developer.mozilla.org/ko/docs/Web/API/Event/target)은 이벤트의 대상 요소_ |
| .[onclick](https://developer.mozilla.org/ko/docs/Web/API/GlobalEventHandlers/onclick) = functionRef\*                                                                             | 대상 클릭 시 함수 호출                                                                                                                                                                                                       |
| .[classList](https://developer.mozilla.org/ko/docs/Web/API/Element/classList)<br>ㅤ.add(String [, String [, ...]])<br>ㅤ.remove(String [, String [, ...]])<br>ㅤ.contains(String) | <br>클래스 추가<br>클래스 삭제<br>클래스 포함 여부                                                                                                                                                                           |
| .[setAttribute](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute)("attribute", "value")<br>.[attribute] = "value"                                            | 속성(HTML) 할당                                                                                                                                                                                                              |
| .[style](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style).[property] = "value"                                                                                 | 특성(CSS) 할당                                                                                                                                                                                                               |
| .[textContent](https://developer.mozilla.org/ko/docs/Web/API/Node/textContent) = "content"                                                                                        | 내용 할당<br>\*_[~~innerText~~](https://developer.mozilla.org/ko/docs/Web/API/HTMLElement/innerText)(보안상 사용 금지)와 유사_                                                                                               |
| .remove()                                                                                                                                                                         | 노드를 메모리에서 삭제                                                                                                                                                                                                       |
| .removeChild(aChild)                                                                                                                                                              | 대상과 자식 노드의 연결을 끊음                                                                                                                                                                                               |
| .children                                                                                                                                                                         | 자식 요소 목록<br>\*_.firstElementChild는 첫 번째 자식_<br>\*_.lastElementChild는 마지막 자식_                                                                                                                               |
| .parentsElement                                                                                                                                                                   | 부모 요소                                                                                                                                                                                                                    |

\*functionRef(Event Handler):

- 함수의 실행이 아닌 함수 자체를 넣어야함
- 아무런 인자를 담지 않으면 event 객체만 전달
- 특정 인자를 전달하기 위해서는 콜백함수 사용  
  ㅤEx. eventHandler={(e) => (param, ..., e) => {}};
- `e.preventDefault();` (고유 동작을 막음)
- `e.stopPropagation();` (이벤트 전파를 막음)
- if (e.target !== e.currentTarget) return; (해당 요소만 이벤트의 대상)

### 2. Scope & Declarations

| Scope                    | Details                                                                                                                                                                                 |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Global Scope             | window(브라우저의 객체)에 저장                                                                                                                                                          |
| ~~Function Level Scope~~ | ~~**var**~~<br/>~~중복 선언 가능~~                                                                                                                                                      |
| Block Level Scope        | **let**<br/>ㅤ중복 선언 불가능<br/>ㅤ값의 재할당 가능<br/>**const**<br/>ㅤ중복 선언 불가능<br/>ㅤ값의 재할당 불가능, 초기화 필수<br/>ㅤ참조형 데이터의 요소는 재할당, 추가, 삭제 가능ㅤ |

\*_하위 스코프 우선(Scope Chaining)_  
\*_선언(호출 X)된 위치에 따라 상위 스코프 결정(Lexical Scoping)_

### 3. This

| Type        | Condition | Target                                                |
| ----------- | --------- | ----------------------------------------------------- |
| 일반 함수   | 호출      | 1. 일반 호출: 전역 객체<br/>2. 메서드 호출: 호출 객체 |
| 화살표 함수 | 선언      | 화살표 함수를 감싸고 있는 외부 함수의 객체            |

<details>
<summary>example</summary>
<div markdown=1>

```js
const obj1 = {
  normal: function () {
    console.log(this);
  },
  arrow: () => {
    console.log(this);
  },
};

obj1.normal(); // 메서드 호출, this === obj1

const obj11 = obj1.normal;
obj11(); // 일반 호출, this === window

obj1.arrow(); // this === { }

// ========== //

const obj2 = {
  normal: function () {
    setTimeout(function () {
      console.log(this);
    }, 1000);
  },
  arrow: function () {
    setTimeout(() => {
      console.log(this);
    }, 1000);
  },
};

obj2.normal(); // this === window
// obj2의 normal을 메서드 호출
// -> normal의 setTimeout함수(내부함수)를 일반 호출

obj2.arrow(); // this === obj2

// ========== //

const obj3 = {
  name: "yuchan",
  outer: function () {
    console.log(this); // --- (1)obj3
    const innerFunc = function () {
      console.log(this); // --- (2)window (3)obj4
    };
    innerFunc(); // --- (2)

    const obj4 = {
      name: "che",
      innerMethod: innerFunc,
    };
    obj4.innerMethod(); // --- (3)
  },
};

obj3.outer(); // --- (1)
// (1)메서드 호출 (2)일반 호출 (3)메서드 호출
```

</div>
</details>

### 4. JSON

| Methods             | Details                               |
| ------------------- | ------------------------------------- |
| JSON.stringify(obj) | obj -> jsonStr, 직렬화(serialize)     |
| JSON.parse(jsonSrt) | jsonStr -> obj, 역직렬화(deserialize) |

\*_JSON(JavaScript Object Notation)문자열은 쌍따옴표("")만 사용 가능_

### 5. Export & Import

```js
// 이름 필수 X, 파일 하나당 하나만 가능
export default 데이터
// 이름 필수 O, 파일 하나당 여러개 가능
export 데이터
```

```js
// export default
import 임의_데이터명 from "경로";
// export
import { 데이터명 } from "경로";
import { 데이터명 as 임의_데이터명 } from "경로";
import * as 임의_객체명 from "경로";
```

### 6. Web Storage(웹 저장소)

- vs Cookie

  - 클라이언트에 정보만 존재 <-> 요청 마다 서버에 함께 전송 (성능 저하 원인, 탈취 위험 높음)
  - 용량 제한이 없음 <-> 있음
  - 만료일이 없음 <-> 있음

- Local Storage

  - 별도로 삭제할 때까지 영구 유지
  - 도메인만 같으면 전역 공유 가능
  - | Methods                              | Details         |
    | ------------------------------------ | --------------- |
    | localStorage.setItem("key", "value") | 데이터 저장     |
    | localStorage.getItem("key")          | 데이터 불러오기 |
    | localStorage.removeItem("key")       | 데이터 삭제     |

- Session Storage

  - 탭이나 브라우저가 종료되면 삭제
  - 같은 도메인이라도 다른 탭이나 브라우저면 공유 불가능

### 7. Map & Set

- Map

  - 객체와 유사한 자료구조
  - symbol이나 string이 아닌 key 사용 가능
  - `for (const [key, value] of map)`
  - WeakMap

    - WeakMap의 key 외에 참조가 없는 객체를 가비지 컬렉팅의 대상으로 만듦
    - 원시형 데이터를 key로 사용 못함
    - 반복작업 및 반복자 객체 반환 메서드를 사용 못함
    - <details>
      <summary>example</summary>
      <div markdown=1>

      ```js
      let user = { name: "adw", age: 29 };

      const userMap = new Map();
      const userWeakMap = new WeakMap();

      userMap.set(user, { married: false });
      userWeakMap.set(user, { married: false });

      user = null;

      console.log(user); // -> null

      console.log(userMap.get(user)); // -> undefined
      console.log(userMap.size); // -> 1

      console.log(userWeakMap.get(user)); // -> undefined
      console.log(userWeakMap.size); // -> undefined
      ```

      </div>
      </details>

- Set
  - 배열과 유사한 자료구조
  - 중복 요소를 가질 수 없음
  - const newArr = [...new Set(arr)]로 배열의 중복 제거 가능
  - `for (const item of set)`

| Properties & Methods | Type     | Details                                                               |
| -------------------- | -------- | --------------------------------------------------------------------- |
| .size                | map, set | 속성/요소의 갯수                                                      |
| .set(key, value)     | map      | 속성 추가, 문자열이 아닌 값도 키로 사용 가능                          |
| .get(key)            | map      | 속성 조회                                                             |
| .add(item)           | set      | 요소 추가                                                             |
| .has(key/item)       | map, set | 해당 속성/요소 존재 여부 확인                                         |
| .delete(key/item)    | map, set | 해당 속성/요소 삭제                                                   |
| .clear()             | map, set | 모든 속성/요소 삭제                                                   |
| .forEach()           | map, set | 모든 속성/요소 삭제                                                   |
| .keys()              | map      | key를 삽입한 순서대로 가지고 있는 iterator(반복자 객체) 반환          |
| .values()            | map      | value를 삽입한 순서대로 가지고 있는 iterator(반복자 객체) 반환        |
| .entries()           | map      | [key, value]를 삽입한 순서대로 가지고 있는 iterator(반복자 객체) 반환 |
