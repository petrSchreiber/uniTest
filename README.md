# uniTest
Unit testing solution for thinBasic.

```
uses "Console"

' -- Include unit test engine
#include "uniTest.tbasicu"

function tbmain()
  ' -- Design the unit test run
  global ut as uniTestRunner()
  
  ut.runTests()
  ut.saveResults(app_sourcepath + "results.txt")
  
  ' -- Present the results your way
  if ut.getFailedCount = 0 then
    printl "All tests have passed" in 10
  else
    printl "Passed: " + ut.getPassedCount in 10
    printl "Failed: " + ut.getFailedCount in 12
    printl
    
    long i
    for i = 1 to ut.getFailedCount
      printl ut.getFailedTestName(i) + ", " + ut.getFailedDescription(i) in 12
    next
  end if
  
  waitkey
  
end function

' -- Write custom tests with predefined asserts
function test_a()
  ut.assertEqual(1, 1)
end function

function test_b()
  ut.assertEqual(1, 2)
end function
```