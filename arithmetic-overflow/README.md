Solidity < 0.8
Integers in Solidity overflow / underflow without any errors

Solidity >= 0.8
Default behaviour of Solidity 0.8 for overflow / underflow is to throw an error.

 This contract is designed to act as a time vault.
 User can deposit into this contract but cannot withdraw for atleast a week.
 User can also extend the wait time beyond the 1 week waiting period.


1. Deploy TimeLock
2. Deploy Attack with address of TimeLock
3. Call Attack.attack sending 1 ether. You will immediately be able to
   withdraw your ether.

What happened?
Attack caused the TimeLock.lockTime to overflow and was able to withdraw
before the 1 week waiting period.

We prevented error using SafeMath from openZeppelin and using it's add function in updating lockTime[msg.sender] to prevent overflow
