
# Slots of storage

In Ethereum, you pay the gas fee for anything storage slot used. because you should be optimizing your code to little storage slot use for costs of little gas. 
When you put two ``` uint128 ``` variables together, the solidity compiler detects them in a 256-bit memory slot and when put not together, each of ``` uint128 ``` variables occupied 256-bit memory. (128-bit memory wasting)

for example, this code is not optimized and will have 3 slot storage used:
```ruby
uint8 a;
uint256 b;
uint8 c;
```
And now look at the below code, variables are packed:
```ruby
uint8 a;
uint8 c;
uint256 b;
```

# Do not shrink Variables without packing
if use the ```unit8``` variables solidity compiler goes to convert ```unit256``` to ```uint8``` and this conversion costs a gas fee. because you should shrink variables when you can pack them.

# Try not to initialize variables with the default value

When you initialize variables with default values costs unnecessary gas.
Like this:
```ruby
bool a = true;
uint b = 0;
```
# Caching array length for loops

Caching the array length outside a loop:

👎 Without Caching: 
```ruby
for (uint256 i = 0; i < array.length; i++) {
}
```
👍 With Caching:
```ruby
uint256 len = array.length
for (uint256 i = 0; i < len; i++) {
}
```
____
More resources:

https://github.com/byterocket/c4-common-issues/blob/main/0-Gas-Optimizations.md/#g001---dont-initialize-variables-with-default-value

https://medium.com/coinmonks/gas-optimization-in-solidity-part-i-variables-9d5775e43dde

https://dev.to/javier123454321/solidity-gas-optimizations-pt-3-packing-structs-23f4

https://yamenmerhi.medium.com/gas-optimization-in-solidity-75945e12322f

