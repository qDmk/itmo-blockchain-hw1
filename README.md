
- MultiSigWallet  
```
24a25
>     uint constant public MAX_ETH_PER_TRANSACTION = 66 ether;
93a95,99
>     modifier validEthValue(uint value) {
>         require(value <= MAX_ETH_PER_TRANSACTION);
>         _;
>     }
>
291a298
>         validEthValue(value)
```

- ERC20
```
32a33,34
>     uint constant private SATURDAY = 1665176400; // sat, 08 oct 2022 00:00:00
> 
210a213,215
>         // Actually a bad idea, since leap second and other problems with date/time.
>         // It worth using a date/time library
>         require(((block.timestamp - SATURDAY) / 1 days) % 7 != 0, "ERC20: can not be transferred on saturdays");
```
- DividentToken
```
21c21
<     event Deposit(address indexed sender, uint256 value);
---
>     event Deposit(address indexed sender, uint256 value, bytes[32] message);
40c40
<     function() external payable {
---
>     function pay_with_message(bytes[32] message) external payable {
42c42
<             emit Deposit(msg.sender, msg.value);
---
>             emit Deposit(msg.sender, msg.value, message);
```