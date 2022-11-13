---
title: "Custom Hooks"
date: 2022-11-07
categories:
  - <summary>
tags:
  - react
---

<details>
<summary><strong>useInput.ts</strong></summary>
<div markdown="1">

```ts
import { useState } from "react";

import type { ChangeEvent, Dispatch, SetStateAction } from "react";

export interface IUseInputResult {
  attribute: {
    value: string;
    placeholder: string;
    onChange: (
      event: ChangeEvent<HTMLInputElement | HTMLTextAreaElement>
    ) => void;
  };
  value: string;
  setValue: Dispatch<SetStateAction<string>>;
}

/**
 * @param initialValue ? 초기값; `""`
 * @param placeholder ? 표시자; `""`
 * @returns `{ attribute, value, setValue }`
 */
export const useInput = (
  initialValue = "",
  placeholder = ""
): IUseInputResult => {
  const [value, setValue] = useState(initialValue);

  const onChange = (
    event: ChangeEvent<HTMLInputElement | HTMLTextAreaElement>
  ): void => {
    setValue(event.target.value);
  };

  return {
    attribute: { value, placeholder, onChange },
    value,
    setValue,
  };
};

// ========== usage ========== //
/*
const exampleInput = useInput("", "")

return (
  <input {...exampleInput.attribute} />` 
)
*/
```

</div>
</details>

<details>
<summary><strong>useRange.ts</strong></summary>
<div markdown="1">

```ts
import { useState } from "react";

import type { ChangeEvent, Dispatch, SetStateAction } from "react";

export interface IUseRangeResult {
  attribute: {
    type: "range";
    value: number;
    min: number;
    max: number;
    step: number;
    onChange: (event: ChangeEvent<HTMLInputElement>) => void;
  };
  value: number;
  setValue: Dispatch<SetStateAction<number>>;
}

/**
 * @param initialValue ? 초기값; `0`
 * @param minValue ? 최솟값; `0`
 * @param maxValue ? 최댓값; `100`
 * @param step ? 단계값; `1`
 * @returns `{ attribute, value, setValue }`
 */
export const useRange = (
  initialValue = 0,
  minValue = 0,
  maxValue = 100,
  step = 1
): IUseRangeResult => {
  const [value, setValue] = useState(initialValue);

  const onChange = (event: ChangeEvent<HTMLInputElement>): void => {
    setValue(Number(event.target.value));
  };

  return {
    attribute: {
      type: "range",
      value,
      min: minValue,
      max: maxValue,
      step,
      onChange,
    },
    value,
    setValue,
  };
};

// ========== usage ========== //
/*
const exampleRange = useRange()

return (
  <input {...exampleRange.attribute} />` 
)
*/
```

</div>
</details>

<details>
<summary><strong>useCheckbox.ts</strong></summary>
<div markdown="1">

```ts
import { useState } from "react";

import type { ChangeEvent, Dispatch, SetStateAction } from "react";

export interface IUseCheckboxResult {
  attribute: {
    type: "checkbox";
    onChange: (event: ChangeEvent<HTMLInputElement>) => void;
  };
  checkedList: string[];
  setCheckedList: Dispatch<SetStateAction<string[]>>;
}

/**
 * @param allList 체크 박스에 포함할 요소 값들
 * @param limit ? 체크 가능 개수; `null`
 * @param initialCheckedList ? 초기에 체크되어 있는 요소 값들; `[]`
 * @returns `{ attribute, checkedList, setCheckedList }`
 */
export const useCheckbox = (
  allList: string[],
  limit: number | null = null,
  initialCheckedList?: string[]
): IUseCheckboxResult => {
  const [checkedList, setCheckedList] = useState(initialCheckedList || []);

  const onChange = (
    event: ChangeEvent<HTMLInputElement | HTMLTextAreaElement>
  ): void => {
    const value = event.target.value;

    if (value === "allCheck") {
      if (limit !== null) return;

      if (checkedList.length === allList.length) {
        setCheckedList([]);
      } else {
        setCheckedList([...allList]);
      }
      return;
    }

    if (checkedList.includes(value)) {
      setCheckedList((prevCheckedList) =>
        prevCheckedList.filter((checkedValue) => checkedValue !== value)
      );
    } else {
      if (limit !== null && checkedList.length >= limit) {
        setCheckedList((prevCheckedList) => [
          ...prevCheckedList.filter((_, idx) => idx !== 0),
        ]);
      }
      setCheckedList((prevCheckedList) => [...prevCheckedList, value]);
    }
  };

  return {
    attribute: { type: "checkbox", onChange },
    checkedList,
    setCheckedList,
  };
};

// ========== usage ========== //
/* 
const EXAMPLES = ["a","b","c"]
const EXAMPLE_LABELS: { [key: string]: string } = {
  "a": "가",
  "b": "나",
  "c": "다",
}
const exampleCheckbox = useCheckbox(EXAMPLES)

return (
  <div>
    <label
      data-is-checked={
        EXAMPLES.length === exampleCheckbox.checkedList.length
      }
    >
    전체 선택
    <input
      {...exampleCheckbox.attribute}
      value="allCheck"
      checked={EXAMPLES.length === exampleCheckbox.checkedList.length}
    />
    </label>
    {EXAMPLES.map((example) => (
      <label
        key={example}
        data-is-checked={exampleCheckbox.checkedList.includes(example)}
      >
      {EXAMPLE_LABELS[example]}
      <input
        {...exampleCheckbox.attribute}
        value={example}
        checked={exampleCheckbox.checkedList.includes(example)}
      />
      </label>
    ))}
    <div>{exampleCheckbox.checkedList}</div>
  </div>
)
*/
/*
input[type="checkbox"] {
  display: none;
}
label {
  ...
  &[data-is-checked="true"] {
    ...
  }
}
*/
```

</div>
</details>

<details>
<summary><strong>useSelect.ts</strong></summary>
<div markdown="1">

```ts
import { useState } from "react";

import type { ChangeEvent, Dispatch, SetStateAction } from "react";

export interface IUseSelectResult {
  attribute: {
    value: string;
    onChange: (event: ChangeEvent<HTMLSelectElement>) => void;
  };
  value: string;
  setValue: Dispatch<SetStateAction<string>>;
}

/**
 * @param initialValue ? 초기값; `""`
 * @returns `{ attribute, value, setValue }`
 */
export const useSelect = (initialValue = ""): IUseSelectResult => {
  const [value, setValue] = useState(initialValue);

  const onChange = (event: ChangeEvent<HTMLSelectElement>) => {
    if (event.target.value !== value) setValue(event.target.value);
  };

  return {
    attribute: { value, onChange },
    value,
    setValue,
  };
};

// ========== usage ========== //
/*
const EXAMPLES = [
  ["a", "가"],
  ["b", "나"],
  ["c", "다"],
]

const exampleSelect = useSelect(EXAMPLES[0][0])

return (
  <select {...exampleSelect.attribute}>
    {EXAMPLES.map((example) => (
      <option key={example[0]} value={example[0]}>
        {example[1]}
      </option>
    ))}
  </ select>
)
*/
```

</div>
</details>

<details>
<summary><strong>useIntersectionObserver.ts</strong></summary>
<div markdown="1">

```ts
import { useEffect, useState } from "react";

import type { RefObject } from "react";

/**
 * @param targetRef 관측 대상
 * @param targetMargin ? 관측 범위; `"0%"`
 * @param isFreezeOnceVisible ? 한번 이상 관측 안 함 여부; `false`
 * @returns 관측 여부
 */
export const useIntersectionObserver = (
  targetRef: RefObject<HTMLDivElement>,
  targetMargin = "0%",
  isFreezeOnceVisible = false
): boolean => {
  const [entry, setEntry] = useState<IntersectionObserverEntry>();

  const isFrozen = entry?.isIntersecting && isFreezeOnceVisible;

  const updateEntry = ([entry]: IntersectionObserverEntry[]): void => {
    setEntry(entry);
  };

  useEffect(() => {
    const target = targetRef?.current;
    const hasIOSupport = !!window.IntersectionObserver;

    if (!hasIOSupport || isFrozen || !target) return;

    const observerParams = {
      threshold: 0,
      root: null,
      rootMargin: targetMargin,
    };
    const observer = new IntersectionObserver(updateEntry, observerParams);

    observer.observe(target);

    return () => observer.disconnect();
  }, [targetRef?.current, targetMargin, isFrozen]);

  return !!entry?.isIntersecting;
};

// ========== usage ========== //
/*
const exampleRef = useRef<HTMLDivElement>(null);
const isVisible = useIntersectionObserver(exampleRef);

return (
  <div>
    <div>{isVisible ? "보임" : "안보임"}</div>
    <div ref={exampleRef}>example</div>
  </div>
)
*/
```

</div>
</details>

<details>
<summary><strong>useDetectOutsideClick.ts</strong></summary>
<div markdown="1">

```ts
import { useState, useEffect } from "react";

import type { Dispatch, SetStateAction, RefObject } from "react";

export type TUseDetectOutsideClickResult = [
  boolean,
  Dispatch<SetStateAction<boolean>>
];

/**
 * @param targetRef 관측 대상
 * @param initialValue ? 초기값; `false`
 * @returns `[isOpen, setIsOpen]`
 * */
export const useDetectOutsideClick = (
  targetRef: RefObject<HTMLDivElement>,
  initialValue = false
): TUseDetectOutsideClickResult => {
  const [isOpen, setIsOpen] = useState(initialValue);

  useEffect(() => {
    const onClick = (event: MouseEvent) => {
      if (
        targetRef.current !== null &&
        !targetRef.current.contains(event.target as Node)
      ) {
        setIsOpen(false);
      }
    };

    if (isOpen) {
      window.addEventListener("click", onClick);
    }

    return () => {
      window.removeEventListener("click", onClick);
    };
  }, [isOpen]);

  return [isOpen, setIsOpen];
};

// ========== usage ========== //
/*
const exampleRef = useRef<HTMLDivElement>(null);
const [isOpen, setIsOpen] = useDetectOutsideClick(exampleRef);

const openModal = () => {
  setIsOpen(true);
};

return (
  <div ref={exampleRef}>
    <div onClick={openModal}>열기</div>
    {isOpen ? <div>모달</div> : null}
  </div>
);
*/
```

</div>
</details>

<details>
<summary><strong>useImageElement.ts</strong></summary>
<div markdown="1">

```ts
import { useEffect, useState } from "react";

export const useImageElement = (
  url: string
): [HTMLImageElement | undefined, boolean] => {
  const [imageElement, setImageElement] = useState<HTMLImageElement>();
  const [isErr, setIsErr] = useState<boolean>(false);

  useEffect(() => {
    const image = new window.Image();
    image.src = url;
    image.crossOrigin = "anonymous";

    image.onload = () => {
      setImageElement(image);
    };

    image.onerror = () => {
      setIsErr(true);
    };
  }, [url]);

  return [imageElement, isErr];
};
```

</div>
</details>
