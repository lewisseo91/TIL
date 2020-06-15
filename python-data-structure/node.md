# python

## node에 필요한 method

## 필요한 method add, desc, remove

class Node:
    def __init__(self, data, next=None):
        self.data = data  # data 입력
        self.next = next # 뒤에꺼 next 설정
        
class NodeMgmt:
    def __init__(self, data):
        self.head = Node(data) # 선 연결
        
    def add(self, data):
        # print(self.head)
        if self.head == None:
            self.head = Node(data)
        elif self.head == '':
            self.head = Node(data)
        else:
            node = self.head
            while node.next:
                node = node.next
            node.next = Node(data)
    
    def desc(self):
        node = self.head
        while node:
            print(node.data)
            node = node.next
            
    def delete(self, data):
        if self.head == '':
            print('can\'t delete');
            return 
        else:
            #3가지 경우 : 처음꺼 삭제, 중간꺼 삭제, 마지막꺼 삭제
            if self.head == None:
                print('No element in Node')
                return
            if self.head.data == data:
                #처음꺼
                temp = self.head  # 지울 것 잠시 저장
                self.head = self.head.next # 다음 것을 head로 만든다.
                del temp
            else:
                # 중간꺼, 마지막꺼 삭제
                node = self.head
                while node.next:
                    if node.next.data == data:
                        temp = node.next # 지울 것 잠시 저장
                        node.next = node.next.next ## 다다음 주소를 next의 저장공간에 넣는다.
                        del temp
                        return
                    else:
                        node = node.next
                    
                    