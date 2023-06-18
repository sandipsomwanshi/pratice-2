# pratice-2
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def addTwoNumbers(l1, l2):
    # Dummy node to store the result
    dummy = ListNode()
    curr = dummy
    carry = 0

    while l1 or l2 or carry:
        # Calculate the sum of the current digits and the carry
        sum_val = carry
        if l1:
            sum_val += l1.val
            l1 = l1.next
        if l2:
            sum_val += l2.val
            l2 = l2.next

        # Update the carry and the digit value for the result
        carry = sum_val // 10
        digit = sum_val % 10

        # Create a new node for the current digit
        curr.next = ListNode(digit)
        curr = curr.next

    return dummy.next

l1 = ListNode(2)
l1.next = ListNode(4)
l1.next.next = ListNode(3)

l2 = ListNode(5)
l2.next = ListNode(6)
l2.next.next = ListNode(4)

# Call the function and print the result
result = addTwoNumbers(l1, l2)

while result:
    print(result.val, end=" ")
    result = result.next
