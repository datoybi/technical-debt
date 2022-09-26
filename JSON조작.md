# JSON 조작

amount 값만 쏙 더하고싶었는데 이렇게 하니까 자꾸 두번계산이 되었다.

```
updatedItems[existItemIndex].amount =
updatedItems[existItemIndex].amount + action.item.amount;
```

그래서 아래와 같은 방법을 써보았다. 잘 작동함을 확인 할 수 있었다.<br>
왜 위의 방법은 안되는지 정확히 설명해보기

```
const updatedItem = {
	...existingCartItem,
	amount: existingCartItem.amount + action.item.amount,
};
```
