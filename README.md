# class-tax
# A new class for tax counting
# Writen in Python
class tax():
    def __init__(self):
        self.list=[]

    def inputcheck(self,*args):
        for i in args:
            if type(i)!=float and type(i)!=int:
                print("Number please!")

    def set(self,key,value):
        for i in range(len(self.list)):
            if self.list[i][0]==key:
                self.list[i][1]=value
                return
        self.list.append([key,value])
        self.list.sort(key=lambda d:d[0])

    def cancel(self,key):
        self.inputcheck(key)
        for i in self.list:
            if i[0]==key:
                self.list.remove(i)
                return
        print("%s did not exist"%str(key))

    def gettax(self,salary):
        self.inputcheck(salary)
        sum=0
        for i in range(len(self.list)):
            if salary >self.list[i][0]:
                sum=sum+(self.list[i][0]-self.list[i-1][0])*self.list[i][1]
            else:
                sum=sum+(salary-self.list[i-1][0])*self.list[i][1]
                return sum
                
    # def add(self,key,value):
    #     for i in self.list:
    #         if i[0]==key:
    #             print("%s has already exist!"%str(key))
    #             return
    #     self.list.append([key,value])
    #     self.list.sort(key=lambda d:d[0])
    #
    # def change(self,key,value):
    #     self.inputcheck(key,value)
    #     for i in self.list:
    #         if i[0]==key:
    #             i[1]=value
    #             return
    #     print("%s did not exit"%str(key))

def main():
    tax1=tax()
    tax1.set(3500, 0)
    tax1.set(5000,0.03)
    tax1.set(83500,0.35)
    tax1.set(10000000,0.3)
    tax1.set(8000,0.1)
    tax1.set(12500,0.3)
    tax1.set(12500,0.2)
    tax1.set(38500,0.25)
    tax1.set(58500,0.3)
    tax1.cancel(58500)
    tax1.set(58500,0.3)
    print(tax1.list)
    print(tax1.gettax(27500))
    print(tax1.gettax(11500))

if __name__=='__main__':
     main()
