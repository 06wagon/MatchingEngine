## **Mini Matching Engine**
This is a mini trading order matching engine for Unix like platform.  
Matching rule is simple: the earlier sent order will be traded earlier if the prices could be matched (buy price not lower than sell price).  
Unit test is handled by Makefile. 

#### **Requirements:**
* C++11
* clang 3.5 / gcc 4.8 or newer

#### **Compiling And Testing:**
To compile:  
`$ make`

To run all unit test cases:  
`$ make test`

Unit test cases for functionality of BUY, SELL, MODIFY, CANCEL, PRINT and Large Scale Test:  
`$ make testbuy`  
`$ make testsell`  
`$ make testmodify`  
`$ make testcancel`  
`$ make testprint`  
`$ make testlarge` or `$ make testlarge TLV=x` (the amount of large scale test could be set with x or left as default value of 50)  

#### **Supported Commands:**

Could take 5 kinds of input from stdin, formats listed below:

1, BUY ORDER\_TYPE QUANTITY PRICE ORDER\_ID; e.g. 'BUY GFD 300 32 u5d12t9'.  
2, SELL ORDER\_TYPE QUANTITY PRICE ORDER\_ID; e.g. 'SELL IOC 300 31 78wehyw'.  
3, MODIFY ORDER\_ID OPERATION\_TYPE QUANTITY PRICE; e.g. 'MODIFY 1d81st2 BUY 200 18'.  
4, CANCEL ORDER\_ID; e.g. 'CANCEL 5z81f72a'.  
5, PRINT; no other parameter.  

There are 2 ORDER\_TYPE, IOC and GFD:  
IOC order (Immediate or Cancel) will not be added to sell/buy list if it was not completely traded.  
GFD order (Good For Day) will be added to sell/buy list if it was not completely traded. 

Order could be partially traded or completely traded. Once a pair of orders (one sell and one buy) got traded, a message will be printed like the following format.  
`TRADE s151h23 1000 20 7sdfa91 1002 20`  

#### License:
See the [License](https://github.com/luo4neck/MatchingEngine/blob/master/LICENSE) file for details. 

//todo dependency issue 

**Jan 2017 @Dublin Ireland**
