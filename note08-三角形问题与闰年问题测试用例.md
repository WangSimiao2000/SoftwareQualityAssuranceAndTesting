# 三角形问题 边界值分析 测试用例

测试用例|a|b|c|预期输出
--|--|--|--|--
test1|60|60|1|等腰三角形
test2|60|60|2|等腰三角形
test3|60|60|60|等边三角形
test4|50|50|99|等腰三角形
test5|50|50|100|非三角形
test6|60|1|60|等腰三角形
test7|60|2|60|等腰三角形
test8|50|99|50|等腰三角形
test9|50|100|50|非三角形
test10|1|60|60|等腰三角形
test11|2|60|60|等腰三角形
test12|99|50|50|等腰三角形
test13|100|50|50|非三角形

```java
Triangle T1 = new Triangle(50, 50, 1);//等腰
Triangle T2 = new Triangle(50, 50, 10);//等腰
Triangle T3 = new Triangle(50, 50, 50);//等边
Triangle T4 = new Triangle(50, 50, 99);//等腰
Triangle T5 = new Triangle(50, 50, 100);//非三角形

Triangle T6 = new Triangle(50, 1, 50);//等腰
Triangle T7 = new Triangle(50, 10, 50);//等腰
Triangle T8 = new Triangle(50, 99, 50);//等腰
Triangle T9 = new Triangle(50, 100, 50);//非三角形

Triangle T10 = new Triangle(1, 50, 50);//等腰
Triangle T11 = new Triangle(10, 50, 50);//等腰
Triangle T12 = new Triangle(99, 50, 50);//等腰
Triangle T13 = new Triangle(100, 50, 50);//非三角形

Triangle T14 = new Triangle(30, 40, 50);//不等边
Triangle T15 = new Triangle(20, 48, 52);//不等边

@Test
public void testIsTriangle() {
	
	assertTrue(T1.isTriangle(T1));
	assertTrue(T2.isTriangle(T2));
	assertTrue(T3.isTriangle(T3));
	assertTrue(T4.isTriangle(T4));
	assertFalse(T5.isTriangle(T5));
	
	assertTrue(T6.isTriangle(T6));
	assertTrue(T7.isTriangle(T7));
	assertTrue(T8.isTriangle(T8));
	assertFalse(T9.isTriangle(T9));
	
	assertTrue(T10.isTriangle(T10));
	assertTrue(T11.isTriangle(T11));
	assertTrue(T12.isTriangle(T12));
	assertFalse(T13.isTriangle(T13));
}

@Test
public void testGetType() {
	//等边
	assertEquals("Regular",T3.getType(T3));
	
	//不等边
	assertEquals("Scalene",T14.getType(T14));
	assertEquals("Scalene",T15.getType(T15));
	
	//等腰
	assertEquals("Isosceles",T1.getType(T1));
	assertEquals("Isosceles",T2.getType(T2));
}

@Test
public void testDiffOfBorders() {
	
	assertEquals((T7.lborderA - T7.lborderB),T7.diffOfBorders(T7.lborderA,T7.lborderB));
	assertEquals((T8.lborderB - T8.lborderA),T8.diffOfBorders(T8.lborderA,T8.lborderB));
	
	assertEquals((T11.lborderB - T11.lborderA),T11.diffOfBorders(T11.lborderA,T11.lborderB));
	assertEquals((T12.lborderA - T12.lborderB),T12.diffOfBorders(T12.lborderA,T12.lborderB));
}
```

# nextdate问题 边界值分析 测试用例

测试用例|month|day|year|预期输出
--|--|--|--|--
test1|6|15|1911|1
test2|6|15|1912|1
test3|6|15|1913|1
test4|6|15|1947|1
test5|6|15|2049|1
test6|6|1|2050|1
test7|6|2|2051|1
test8|6|-1|2001|
test9|6|1|2001|
test10|6|2|2001|
test11|6|30|2001|
test12|6|31|2001|
test13|6|32|2001|
test14|-1|15|2001|
test15|1|15|2001|
test16|2|15|2001|
test17|11|15|2001|
test18|12|15|2001|
test19|13|15|2001|

# 闰年问题

```java
//测试输入年份与1582年的关系
assertEquals("after1582",LeapYearJudge.isTrueInput(2000));
assertEquals("after1582",LeapYearJudge.isTrueInput(1582));
assertEquals("before1582",LeapYearJudge.isTrueInput(1581));
assertEquals("before1582",LeapYearJudge.isTrueInput(-1));
		
//测试输入的1582年以来的年分是否是闰年
assertTrue(LeapYearJudge.isLeapYearA(10000));
assertTrue(LeapYearJudge.isLeapYearA(2000));
assertTrue(LeapYearJudge.isLeapYearA(1584));
assertFalse(LeapYearJudge.isLeapYearA(1582));
assertFalse(LeapYearJudge.isLeapYearA(2021));
		
//测试输入的1582年之前的年分是否是闰年
assertTrue(LeapYearJudge.isLeapYearB(1580));
assertTrue(LeapYearJudge.isLeapYearB(-5));
assertTrue(LeapYearJudge.isLeapYearB(0));
assertFalse(LeapYearJudge.isLeapYearB(1581));
assertFalse(LeapYearJudge.isLeapYearB(-3));
assertFalse(LeapYearJudge.isLeapYearB(-4));
```
