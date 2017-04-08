### ArrayList：

**1**.**add是将传入的参数作为当前List中的一个Item存储，即使你传入一个List也只会另当前的List增加1个元素  
addAll是传入一个List，将此List中的所有元素加入到当前List中，也就是当前List会增加的元素个数为传入的List的大小**

eg:

Collection result = new ArrayList\(\);  
Collection list = new ArrayList\(\);

......

分析：

result.addAll\(list\);//把list中的每一个元素加到result中，result.size\(\)==list.size\(\)

result.add\(list\);//将list作为一个元素加到result中，则result.size\(\)为1

**2**. results.remove\( index\);// 除去index 位置的元素，

results.size\(\) // 求此arraylist 的长度



