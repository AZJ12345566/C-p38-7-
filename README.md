# C-p38-7-
C 语言学习笔记 p38指针详解(7)
#include<stdio.h>
//qsort第一个参数：待排序数组的首元素地址
//第二个参数：待排序数组的元素个数
//第三个参数：待排序数组的每个元素的大小-单位是字节
//第四个参数：是函数指针，比较两个元素的所用函数的地址-这个函数使用者自己实现函数指针的两个参数是：待比较两个元素的地址

void Swap(char* buf1,char* buf2,int width)
{
    int i=0;
    for(i=0;i<width;i++)
    {
        char tmp=*buf1;
        *buf1=*buf2;
        *buf2=tmp;
        buf1++;
        buf2++;
    }
}
void bubble_sort(void* base,int sz,int width,int (*cmp)(void* e1,void* e2))
{
    int i=0;
    //趟数
    for(i=0;i<sz;i++)
    {
        //每一趟比较的对数
        int j=0;
        for(j=0;j<sz-1-i;j++)
        {
            //两个元素的比较
            if(cmp((char*)base+j*width,(char*)base+(j+1)*width)>0)
            {
                //交换
                Swap((char*)base+j*width,(char*)base+(j+1)*width),width);
            }
        }
    }
}
void test4()
{
    int arr[10]={9,8,7,6,5,4,3,2,1,0};
    int sz=sizeof(arr)/sizeof(arr[0]);
    //使用bubble_sort的程序员一定知道自己排序的是什么数据
    //就应该知道如何比较待排序数组中的元素
    bubble_sort(arr,szz,sizoef(arr[0]),cmp_int);
}

cmp_stu_by_name(const void*e1,const coid* e2)
{
    //比较名字就是比较字符串
    //字符串不能直接用<>=来进行比较，应该用strcmp函数
    return strcmp(((struct Stu*)e1)->name,((struct Stu*)e2)->name);
}
void test5()
{
    struct Stu s[3]={{"zhangsan",20},{"lisi",30},{"wangwu",10}};
    int sz=sizeof(s)/sizeof(s[0]);
    bubble_sort(s,sizeof(s[0]),cmp_stu_by_name);
}
int main()
{
    test4();
    test5();
    return 0;
}
