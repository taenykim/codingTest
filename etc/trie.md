## Trie

https://wiki.jieunkim.site/Algorithm/01.trie.html#trie-%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7 을 보고 JavaScript로 코드를 변경해보았다!

자세한 설명은 👆링크 참조!

```js
function makeTrie(words) {
  const root = {};
  let current;
  for (const word of words) {
    current = root;
    for (const letter of word) {
      if (!current[letter]) current[letter] = [0, {}];
      current[letter][0] += 1;
      current = current[letter][1];
    }
  }
  return root;
}

function solution(words) {
  let answer = 0;
  const trie = makeTrie(words);
  //   console.dir(trie, { depth: null })

  let curTrie;

  for (const word of words) {
    curTrie = trie;
    let i = 0;
    for (i = 0; i < word.length - 1; i++) {
      if (curTrie[word[i]][0] === 1) {
        break;
      }
      curTrie = curTrie[word[i]][1];
    }
    answer += i + 1;
  }
  return answer;
}

const input = ["word", "war", "warrior", "world"];
console.log(solution(input));
```

```js
// 만들어지는 트리의 형태
const tree = {
  w: [
    4,
    {
      o: [
        2,
        {
          r: [
            2,
            {
              d: [1, {}],
              l: [1, { d: [1, {}] }],
            },
          ],
        },
      ],
      a: [
        2,
        {
          r: [
            2,
            {
              r: [
                1,
                {
                  i: [
                    1,
                    {
                      o: [1, { r: [1, {}] }],
                    },
                  ],
                },
              ],
            },
          ],
        },
      ],
    },
  ],
};
```
