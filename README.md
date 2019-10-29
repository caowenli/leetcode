# leetcode
算法题
3.数组中重复的数字
分析：n个数据：数据大小为0-n-1
python版本：
时间复杂度：o(n)
空间复杂度：o(n)
方法1:使用collections.Counter()相当于字典的wordcount
import collections
class Solution:
    def duplicate(self, numbers, duplication):
        flag = False
        count_dict = collections.Counter(numbers)
        for k, v in count_dict.items():
            if v > 1:
                duplication[0] = k
                flag = True
                break
        return flag
方法2:根据题中的条件,数据和下标一一对应的原则是调整
时间复杂度：o(n)
空间复杂度：o(1)
class Solution:
    def duplicate(self, numbers, duplication):
        flag = False
        for i, v in enumerate(numbers):
            current = v
            if current != i:
                if numbers[v] == v:
                    flag = True
                    duplication[0] = v
                    break
                else:
                    numbers[i] = numbers[v]
                    numbers[v] = current
        return flag
4. 二维数组中的查找
方法1:暴力法直接找：
时间复杂度：o(n**2)
空间复杂度：o(1)
class Solution:
    def Find(self, target, array):
        flag=False
        for row in range(len(array)):
            for col in range(len(array[0])):
                if array[row][col]==target:
                    flag=True
                    break
        return flag
方法2:根据分析根据题中的意思数据的从左到右，从上到下是递增的:
时间复杂度：o(n**2)
空间复杂度：o(1)
class Solution:
    def Find(self, target, array):
        flag = False
        row = len(array) - 1
        col = 0
        while row >= 0 and col <= len(array[0]) - 1:
            if array[row][col] == target:
                flag = True
                break
            elif array[row][col] > target:
                row = row - 1
            else:
                col = col + 1
        return flag
5. 替换空格
方法1：先将字符串转成list，判断后转为list。
时间复杂度：o(n)
空间复杂度：o(1)
class Solution:
    def replaceSpace(self, s):
        s_list = list(s)
        for i, v in enumerate(s_list):
            if v == ' ':
                s_list[i] = '%20'
        return ''.join(s_list)
6. 从尾到头打印链表
方法1:建立一个list，头部插入的方法进行
时间复杂度：o(n)
空间复杂度：o(n)
class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        res = []
        head = listNode
        while head:
            res.insert(0, head.val)
            head = head.next
        return res
方法2:建立一个list,插入head中元素然后再反转
class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        res = []
        head = listNode
        while head:
            res.append(head.val)
            head = head.next
        return res[::-1]
方法3：建立一个list,插入head中元素然后再反转
class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        res = []
        head = listNode
        while head:
            res.append(head.val)
            head = head.next
        res.reverse()
        return res
