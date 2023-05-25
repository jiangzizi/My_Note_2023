# 工厂方法
```c++
#include<iostream>
#include<vector>
using namespace std;
class animal
{
    public:
        virtual void show()=0;
};
class farm
{
    public:
        virtual void newanimal()=0;
};
class horse:public animal
{
    public:
        horse()
        {
            std::cout<<"New horse born!"<<endl;
        }
        void show() override
        {
            std::cout<<"This is a horse!"<<endl;
        }

};
class cow:public animal
{
    public:
        cow()
        {
            std::cout<<"New cow born!"<<endl;
        }
        void show() override
        {
            std::cout<<"This is a cow!"<<endl;
        }
};
class horsefarm:public farm
{
    private:
        vector<horse> arr;
    public:
        horsefarm()
        {
            std::cout<<"horsefarm created!"<<endl;
        }
        void newanimal()override
        {
            arr.push_back(horse());
        }
};
class cowfarm:public farm
{
    private:
        vector<cow> arr;
    public:
        cowfarm()
        {
            std::cout<<"cowfarm created!"<<endl;
        }
        void newanimal()override
        {
            arr.push_back(cow());
        }
};

int main()
{
    cowfarm myfarm;
    myfarm.newanimal();
    return 0;
}
```


>【例】用工厂方法模式设计畜牧场。

>分析：有很多种类的畜牧场，如养马场用于养马，养牛场用于养牛，所以该实例用工厂方法模式比较适合。

>对养马场和养牛场等具体工厂类，只要定义一个生产动物的方法 newAnimal() 即可。其结构图如图2-5所示。
# 抽象工厂
```c++
#include<iostream>
using namespace std;
class plant
{
    public:
    virtual void newplant()=0;
};
class animal
{
    public:
    virtual void newanimal()=0;
};
class yard
{
    public:
    virtual void newyard()=0;
};
class plantA:public plant
{
    public:
        void newplant() override
        {
            std::cout<<"plantA grow!!"<<endl;
        }
};
class plantB:public plant
{
    public:
        void newplant() override
        {
            std::cout<<"plantB grow!!"<<endl;
        }
};
class animalA:public animal
{
    public:
     void newanimal() override
     {
        cout<<"animalA grow!!"<<endl;
     }
};
class animalB:public animal
{
    public:
     void newanimal() override
     {
        cout<<"animalB grow!!"<<endl;
     }
};
class yardA:public yard
{
    public:
    void newyard()override
    {
    }

};
```

>例：用抽象工厂模式设计农场类。

>分析：农场中除了畜牧场一样可以养动物，还可以培养植物，如养马、养牛、种菜、种水果等，所以本实例比签名介绍的畜牧场类复杂，必须用抽象工厂模式来实现。

>本例用抽象工厂模式来设计两个农场，一个是韶关农场用于养牛和种菜，一个是上饶农场用于养马和种水果，可以在以上两个农场中定义一个生产动物的方法 newAnimal() 和一个培养的方法 newPlant()。其结构如图2-8所示。
