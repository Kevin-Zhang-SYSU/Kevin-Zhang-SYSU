//体测成绩管理系统

#include <stdio.h>
#include <string.h>
int num;//定义学生个数为全局变量
float boy[10][100] = { {17.8,24,28} ,{2300,2460,2620,2780,2940,3100,3700,4300,4800,5040},\
	   {6.7,6.9,7.1,8.1,9.1,9.3,9.5,9.7,9.9,10.1},{183,188,193,198,203,206,228,248,263,273},\
	   {-1.3,-0.3,0.7,1.7,2.7,3.7,10.7,17.7,21.3,24.9},{3.17,3.27,3.42,4.07,4.32,4.52,5.12,5.32,5.52,6.12},\
	   {5,6,7,8,9,10,12.5,15,17,19} };//定义男生体测成绩的各项标准
float girl[10][100] = { {17.1,24,28},{1800,1840,1880,1920,1960,2000,2500,3000,3300,3400},\
	   {7.5,7.7,8.3,9.3,10.3,10.5,10.7,10.9,11.1,11.3},{126,131,136,141,146,151,166,181,195,207},\
	   {2.0,2.8,3.6,4.4,5.2,6.0,12.5,19.0,22.2,25.8},{3.18,3.24,3.30,3.44,4.09,4.34,4.44,4.54,5.04,5.14,5.24},\
	   {16,18,20,22,24,26,36,46,52,56} };//定义女生体测成绩的各项标准
struct Student
{
	int ID;
	char name[20];
	char sex[10];
	float height;
	float weight;
	int lc;
	float dash;
	float jump;
	float sr;
	float dis_race;
	int pu_su;
	float BMI;
	float total;
};
int main()
{
	void get(struct Student a[]);//输入学生信息
	void sum(struct Student a[]);//计算体测总成绩函数
	void sort_total(struct Student a[]);//根据体测成绩由高到低排名
	void sort_ID(struct Student a[]);//根据学号由小到大排名
	void search_name(struct Student a[]);//根据姓名查找成绩
	void search_ID(struct Student a[]);//根据学号查找成绩
	void sort_each(struct Student a[]);//对每一单项进行排名
	void data(struct Student a[]);//对成绩的各项数据分析
	int i = 0, j = 0;
	printf("请输入你要管理的的学生个数：");
	scanf_s("%d", &num);
	printf("\n");
	struct Student stu[100];
	get(stu);//输入学生信息
	printf("\n");
	sum(stu);
	printf("\n");
	while (1)
	{
		int function = 0;
		printf("*************************\n");
		printf("1.根据总成绩由高到低排名\n2.根据学号由小到大排名\n3.根据姓名查找成绩\n4.根据学号查找成绩\n5.对单项成绩进行排名\n6.对成绩的各项数据分析\n7.结束\n");
		printf("*************************\n");
		printf("请输入你要进行的操作：");
		scanf_s("%d", &function);
		if (function == 7)break;
		switch (function)
		{
		case 1:sort_total(stu); break;
		case 2:sort_ID(stu); break;
		case 3:search_name(stu); break;
		case 4:search_ID(stu); break;
		case 5:sort_each(stu); break;
		case 6:data(stu); break;
		default:printf("无效数据，请重新输入！");
		}
		printf("\n");
	}
	return 0;
}
void get(struct Student a[])
{
	int i;
	printf("请以：学号 姓名 性别 身高(cm) 体重(kg) 肺活量(ml) 50米短跑(s) 立定跳远(cm) 坐位体前屈(cm) \
800米/1000米长跑(min.s) 一分钟仰卧起坐(次)/引体向上(次)的形式输入学生信息\n");
	for (i = 0; i < num; i++)
		scanf_s("%d %s %s %f %f %d %f %f %f %f %d", \
			& a[i].ID, a[i].name, 20, a[i].sex, 10, &a[i].height, &a[i].weight, &a[i].lc, \
			& a[i].dash, &a[i].jump, &a[i].sr, &a[i].dis_race, &a[i].pu_su);
	printf("\n");
	struct Student* p;
	printf("您输入的成绩为：\n");
	for (p = a; p < a + num; p++)
		printf("%d %s %s %.2f %.2f %d %.2f %.2f %.2f %.2f %d\n", (*p).ID, (*p).name, (*p).sex, \
			(*p).height, (*p).weight, (*p).lc, (*p).dash, (*p).jump, (*p).sr, (*p).dis_race, (*p).pu_su);
	printf("\n");
}
void sum(struct Student a[])
{
	int i = 0, j = 0, total = 0;
	int qcj(float x, float b[10], int flag);
	int s1, s2, s3, s4, s5, s6, s7;
	for (i = 0; i < num; i++)
		a[i].BMI = a[i].weight / a[i].height * 100 / a[i].height * 100;//计算BMI指数
	for (i = 0; i < num; i++)
		if (strcmp(a[i].sex, "男") == 0)
		{
			if (a[i].BMI < boy[0][0] || a[i].BMI>boy[0][1] && a[i].BMI < boy[0][2]) s1 = 80;
			else if (a[i].BMI > boy[0][0] && a[i].BMI < boy[0][1]) s1 = 100;
			else if (a[i].BMI > boy[0][2]) s1 = 60;
			s2 = qcj(a[i].lc, boy[1], 0);
			s3 = qcj(a[i].dash, boy[2], 1);
			s4 = qcj(a[i].jump, boy[3], 0);
			s5 = qcj(a[i].sr, boy[4], 0);
			s6 = qcj(a[i].dis_race, boy[5], 1);
			s7 = qcj(a[i].pu_su, boy[6], 0);
			a[i].total = 0.15 * s1 + 0.15 * s2 + 0.2 * s3 + 0.1 * s4 + 0.1 * s5 + 0.2 * s6 + 0.1 * s7;
		}
		else
		{
			if (a[i].BMI < girl[0][0] || a[i].BMI>girl[0][1] && a[i].BMI < girl[0][2]) s1 = 80;
			else if (a[i].BMI > girl[0][0] && a[i].BMI < girl[0][1]) s1 = 100;
			else if (a[i].BMI > girl[0][2]) s1 = 60;
			s2 = qcj(a[i].lc, girl[1], 0);
			s3 = qcj(a[i].dash, girl[2], 1);
			s4 = qcj(a[i].jump, girl[3], 0);
			s5 = qcj(a[i].sr, girl[4], 0);
			s6 = qcj(a[i].dis_race, girl[5], 1);
			s7 = qcj(a[i].pu_su, girl[6], 0);
			a[i].total = 0.15 * s1 + 0.15 * s2 + 0.2 * s3 + 0.1 * s4 + 0.1 * s5 + 0.2 * s6 + 0.1 * s7;
		}
	printf("整理后的成绩为：\n学号 姓名 性别 身高(cm) 体重(kg) 肺活量(ml) 50米短跑(s) 立定跳远(cm) \
坐位体前屈(cm) 800米/1000米长跑(min.s) 一分钟仰卧起坐(次)/引体向上(次) BMI 体测总成绩\n");
	for (i = 0; i < num; i++)
	{
		printf("%d %s %s %.2f %.2f %d %.2f %.2f %.2f %.2f %d %.2f %.2f\n", a[i].ID, a[i].name, a[i].sex, \
			a[i].height, a[i].weight, a[i].lc, a[i].dash, a[i].jump, a[i].sr, a[i].dis_race, \
			a[i].pu_su, a[i].BMI, a[i].total);
	}
}
int qcj(float x, float b[10], int flag)
{
	if (x <= b[0]) return flag == 0 ? 10 : 100;
	if (x <= b[1]) return flag == 0 ? 20 : 90;
	if (x <= b[2]) return flag == 0 ? 30 : 80;
	if (x <= b[3]) return flag == 0 ? 40 : 70;
	if (x <= b[4]) return flag == 0 ? 50 : 60;
	if (x <= b[5]) return flag == 0 ? 60 : 50;
	if (x <= b[6]) return flag == 0 ? 70 : 40;
	if (x <= b[7]) return flag == 0 ? 80 : 30;
	if (x <= b[8]) return flag == 0 ? 90 : 20;
	if (x > b[8]) return flag == 0 ? 100 : 10;
}
void sort_total(struct Student a[])
{
	int i = 0, k = 0;
	struct Student temp;
	for (k = 0; k < num - 1; k++)
	{
		for (i = 0; i < num - k - 1; i++)//冒泡排序法
		{
			if (a[i].total < a[i + 1].total)
			{
				temp = a[i];
				a[i] = a[i + 1];
				a[i + 1] = temp;
			}
		}
	}
	printf("按体测成绩排名由高到低排序：\n");
	for (i = 0; i < num; i++)
	{
		printf("%d %s %s %.2f %.2f %d %.2f %.2f %.2f %.2f %d %.2f %.2f\n", a[i].ID, a[i].name, a[i].sex, \
			a[i].height, a[i].weight, a[i].lc, a[i].dash, a[i].jump, a[i].sr, a[i].dis_race, \
			a[i].pu_su, a[i].BMI, a[i].total);
	}
}
void sort_ID(struct Student a[])
{
	int i = 0, k = 0;
	struct Student temp;
	for (k = 0; k < num - 1; k++)
	{
		for (i = 0; i < num - k - 1; i++)//冒泡排序法
		{
			if (a[i].ID > a[i + 1].ID)
			{
				temp = a[i];
				a[i] = a[i + 1];
				a[i + 1] = temp;
			}
		}
	}
	printf("按学生学号由小到大排序：\n");
	for (i = 0; i < num; i++)
	{
		printf("%d %s %s %.2f %.2f %d %.2f %.2f %.2f %.2f %d %.2f %.2f\n", a[i].ID, a[i].name, a[i].sex, \
			a[i].height, a[i].weight, a[i].lc, a[i].dash, a[i].jump, a[i].sr, a[i].dis_race, \
			a[i].pu_su, a[i].BMI, a[i].total);
	}
}
void search_name(struct Student a[])
{
	int i;
	char z[30] = { '\0' };
	printf("请输入要查找的学生姓名：");
	scanf_s("%s", z, 30);
	for (i = 0; i < num; i++)
	{
		if (strcmp(z, a[i].name) == 0) break;
	}
	if (i == num)printf("查无此人！\n");
	else
	{
		printf("所对应学生的成绩为：\n");
		printf("%d %s %s %.2f %.2f %d %.2f %.2f %.2f %.2f %d %.2f %.2f\n", a[i].ID, a[i].name, a[i].sex, \
			a[i].height, a[i].weight, a[i].lc, a[i].dash, a[i].jump, a[i].sr, a[i].dis_race, \
			a[i].pu_su, a[i].BMI, a[i].total);
	}
}
void search_ID(struct Student a[])
{
	int i;
	int id = 0;
	printf("请输入要查找的学号：");
	scanf_s("%d", &id);
	for (i = 0; i < num; i++)
	{
		if (id == a[i].ID) break;
	}
	if (i == num)printf("查无此人！\n");
	else
	{
		printf("所对应学生的成绩为：\n");
		printf("%d %s %s %.2f %.2f %d %.2f %.2f %.2f %.2f %d %.2f %.2f\n", a[i].ID, a[i].name, a[i].sex, \
			a[i].height, a[i].weight, a[i].lc, a[i].dash, a[i].jump, a[i].sr, a[i].dis_race, \
			a[i].pu_su, a[i].BMI, a[i].total);
	}
}
void sort_each(struct Student a[])
{
	char sex;
	int i = 0, k = 0;
	int boy, girl;
	struct Student temp;
	printf("请选择你要查看的性别：A.男  B.女\n");
	getchar();
	scanf_s("%c", &sex, 1);
	if (sex == 'A')
	{
		printf("请选择你要查看的单项成绩排名：\n");
		printf("1.BMI  2.肺活量  3.短跑  4.跳远  5.体前屈  6.长跑  7.引体向上\n");
		scanf_s("%d", &boy);
		printf("该单项成绩排名为：\n");
		switch (boy)
		{
		case 1:
		{
			for (k = 0; k < num - 1; k++)
				for (i = 0; i < num - k - 1; i++)
					if (a[i].BMI < a[i + 1].BMI)
					{
						temp = a[i];
						a[i] = a[i + 1];
						a[i + 1] = temp;
					}
			for (i = 0; i < num; i++)
			{
				if (strcmp(a[i].sex, "男") == 0)
				{
					printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].BMI);
				}
			}
			break;
		}
		case 2:
		{
			for (k = 0; k < num - 1; k++)
				for (i = 0; i < num - k - 1; i++)
					if (a[i].lc < a[i + 1].lc)
					{
						temp = a[i];
						a[i] = a[i + 1];
						a[i + 1] = temp;
					}
			for (i = 0; i < num; i++)
			{
				if (strcmp(a[i].sex, "男") == 0)
				{
					printf("%d %s %s %d\n", a[i].ID, a[i].name, a[i].sex, a[i].lc);
				}
			}
			break;
		}
		case 3:
		{
			for (k = 0; k < num - 1; k++)
				for (i = 0; i < num - k - 1; i++)
					if (a[i].dash > a[i + 1].dash)
					{
						temp = a[i];
						a[i] = a[i + 1];
						a[i + 1] = temp;
					}
			for (i = 0; i < num; i++)
			{
				if (strcmp(a[i].sex, "男") == 0)
				{
					printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].dash);
				}
			}
			break;
		}
		case 4:
		{
			for (k = 0; k < num - 1; k++)
				for (i = 0; i < num - k - 1; i++)
					if (a[i].jump < a[i + 1].jump)
					{
						temp = a[i];
						a[i] = a[i + 1];
						a[i + 1] = temp;
					}
			for (i = 0; i < num; i++)
			{
				if (strcmp(a[i].sex, "男") == 0)
				{
					printf("%d %s %s %.1f\n", a[i].ID, a[i].name, a[i].sex, a[i].jump);
				}
			}
			break;
		}
		case 5:
		{
			for (k = 0; k < num - 1; k++)
				for (i = 0; i < num - k - 1; i++)
					if (a[i].sr < a[i + 1].sr)
					{
						temp = a[i];
						a[i] = a[i + 1];
						a[i + 1] = temp;
					}
			for (i = 0; i < num; i++)
			{
				if (strcmp(a[i].sex, "男") == 0)
				{
					printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].sr);
				}
			}
			break;
		}
		case 6:
		{
			for (k = 0; k < num - 1; k++)
				for (i = 0; i < num - k - 1; i++)
					if (a[i].dis_race > a[i + 1].dis_race)
					{
						temp = a[i];
						a[i] = a[i + 1];
						a[i + 1] = temp;
					}
			for (i = 0; i < num; i++)
			{
				if (strcmp(a[i].sex, "男") == 0)
				{
					printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].dis_race);
				}
			}
			break;
		}
		case 7:
		{
			for (k = 0; k < num - 1; k++)
				for (i = 0; i < num - k - 1; i++)
					if (a[i].pu_su < a[i + 1].pu_su)
					{
						temp = a[i];
						a[i] = a[i + 1];
						a[i + 1] = temp;
					}
			for (i = 0; i < num; i++)
			{
				if (strcmp(a[i].sex, "男") == 0)
				{
					printf("%d %s %s %d\n", a[i].ID, a[i].name, a[i].sex, a[i].pu_su);
				}
			}
			break;
		}
		default:printf("无效数据，请重新输入！");
		}
	}
	else
		if (sex == 'B')
		{
			printf("请选择你要查看的单项成绩排名：\n");
			printf("1.BMI  2.肺活量  3.短跑  4.跳远  5.体前屈  6.长跑  7.仰卧起坐\n");
			scanf_s("%d", &girl);
			printf("该单项成绩排名为：\n");
			switch (girl)
			{
			case 1:
			{
				for (k = 0; k < num - 1; k++)
					for (i = 0; i < num - k - 1; i++)
						if (a[i].BMI < a[i + 1].BMI)
						{
							temp = a[i];
							a[i] = a[i + 1];
							a[i + 1] = temp;
						}
				for (i = 0; i < num; i++)
				{
					if (strcmp(a[i].sex, "女") == 0)
					{
						printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].BMI);
					}
				}
				break;
			}
			case 2:
			{
				for (k = 0; k < num - 1; k++)
					for (i = 0; i < num - k - 1; i++)
						if (a[i].lc < a[i + 1].lc)
						{
							temp = a[i];
							a[i] = a[i + 1];
							a[i + 1] = temp;
						}
				for (i = 0; i < num; i++)
				{
					if (strcmp(a[i].sex, "女") == 0)
					{
						printf("%d %s %s %d\n", a[i].ID, a[i].name, a[i].sex, a[i].lc);
					}
				}
				break;
			}
			case 3:
			{
				for (k = 0; k < num - 1; k++)
					for (i = 0; i < num - k - 1; i++)
						if (a[i].dash > a[i + 1].dash)
						{
							temp = a[i];
							a[i] = a[i + 1];
							a[i + 1] = temp;
						}
				for (i = 0; i < num; i++)
				{
					if (strcmp(a[i].sex, "女") == 0)
					{
						printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].dash);
					}
				}
				break;
			}
			case 4:
			{
				for (k = 0; k < num - 1; k++)
					for (i = 0; i < num - k - 1; i++)
						if (a[i].jump < a[i + 1].jump)
						{
							temp = a[i];
							a[i] = a[i + 1];
							a[i + 1] = temp;
						}
				for (i = 0; i < num; i++)
				{
					if (strcmp(a[i].sex, "女") == 0)
					{
						printf("%d %s %s %.1f\n", a[i].ID, a[i].name, a[i].sex, a[i].jump);
					}
				}
				break;
			}
			case 5:
			{
				for (k = 0; k < num - 1; k++)
					for (i = 0; i < num - k - 1; i++)
						if (a[i].sr < a[i + 1].sr)
						{
							temp = a[i];
							a[i] = a[i + 1];
							a[i + 1] = temp;
						}
				for (i = 0; i < num; i++)
				{
					if (strcmp(a[i].sex, "女") == 0)
					{
						printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].sr);
					}
				}
				break;
			}
			case 6:
			{
				for (k = 0; k < num - 1; k++)
					for (i = 0; i < num - k - 1; i++)
						if (a[i].dis_race > a[i + 1].dis_race)
						{
							temp = a[i];
							a[i] = a[i + 1];
							a[i + 1] = temp;
						}
				for (i = 0; i < num; i++)
				{
					if (strcmp(a[i].sex, "女") == 0)
					{
						printf("%d %s %s %.2f\n", a[i].ID, a[i].name, a[i].sex, a[i].dis_race);
					}
				}
				break;
			}
			case 7:
			{
				for (k = 0; k < num - 1; k++)
					for (i = 0; i < num - k - 1; i++)
						if (a[i].pu_su < a[i + 1].pu_su)
						{
							temp = a[i];
							a[i] = a[i + 1];
							a[i + 1] = temp;
						}
				for (i = 0; i < num; i++)
				{
					if (strcmp(a[i].sex, "女") == 0)
					{
						printf("%d %s %s %d\n", a[i].ID, a[i].name, a[i].sex, a[i].pu_su);
					}
				}
				break;
			}
			default:printf("无效数据，请重新输入！");
			}
		}
		else
		{
			printf("无效数据，请重新输入！");
		}
}
void data(struct Student a[])
{
	float sum;
	char sex;
	int num1 = 0, num2 = 0, j = 0;
	for (j = 0; j < num; j++)
	{
		if (strcmp(a[j].sex, "男") == 0)
		{
			num1 = num1 + 1;
		}
		else num2++;
	}
	printf("学生中男生有%d人，女生有%d人\n", num1, num2);
	int i = 0, k = 0, s1, s2;
	float temp = 0, p = 0;
	float b[500];
	float mean(float number[], int s);//声明求平均数函数
	float median(float number[], int s);//声明求众数函数
	printf("请选择你要查看的性别：A.男  B.女\n");
	getchar();
	scanf_s("%c", &sex, 1);
	if (sex == 'A')
	{
		printf("1.BMI  2.肺活量  3.短跑  4.跳远  5.体前屈  6.长跑  7.引体向上  8.总成绩\n");
		printf("请选择你要查看数据的项目：");
		scanf_s("%d", &i);
		switch (i)
		{
		case 1:
		{
			for (j = 0; j < num; j++)
			{
				if (strcmp(a[j].sex, "男") == 0)
				{
					b[j] = a[j].BMI;
				}
			}
			temp = mean(b, num1);
			p = median(b, num1);
			if (temp < boy[0][0] || temp>boy[0][1] && temp < boy[0][2]) s1 = 80;
			else if (temp > boy[0][0] && temp < boy[0][1]) s1 = 100;
			else if (temp > boy[0][2]) s1 = 60;
			if (p < boy[0][0] || p>boy[0][1] && p < boy[0][2]) s2 = 80;
			else if (p > boy[0][0] && p < boy[0][1]) s2 = 100;
			else if (p > boy[0][2]) s2 = 60;
			printf("平均数为：%.2f  对应的成绩为：%d\n", temp, s1);
			printf("中位数为：%.2f  对应的成绩为：%d\n", p, s2);
			break;
		}
		case 2:
		{
			for (j = 0; j < num; j++)
			{
				if (strcmp(a[j].sex, "男") == 0)
				{
					b[j] = a[j].lc;
				}
			}
			printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num1), qcj(mean(b, num1), boy[1], 0));
			printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num1), qcj(median(b, num1), boy[1], 0));
			break;
		}
		case 3:
		{
			for (j = 0; j < num; j++)
			{
				if (strcmp(a[j].sex, "男") == 0)
				{
					b[j] = a[j].dash;
				}
			}
			printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num1), qcj(mean(b, num1), boy[2], 1));
			printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num1), qcj(median(b, num1), boy[2], 1));
			break;
		}
		case 4:
		{
			for (j = 0; j < num; j++)
			{
				if (strcmp(a[j].sex, "男") == 0)
				{
					b[j] = a[j].jump;
				}
			}
			printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num1), qcj(mean(b, num1), boy[3], 0));
			printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num1), qcj(median(b, num1), boy[3], 0));
			break;
		}
		case 5:
		{
			for (j = 0; j < num; j++)
			{
				if (strcmp(a[j].sex, "男") == 0)
				{
					b[j] = a[j].sr;
				}
			}
			printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num1), qcj(mean(b, num1), boy[4], 0));
			printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num1), qcj(median(b, num1), boy[4], 0));
			break;
		}
		case 6:
		{
			for (j = 0; j < num; j++)
			{
				if (strcmp(a[j].sex, "男") == 0)
				{
					b[j] = a[j].dis_race;
				}
			}
			printf("平均数为：%.2f  对应的成绩为：%d\n", mean(b, num1), qcj(mean(b, num1), boy[5], 1));
			printf("中位数为：%.2f  对应的成绩为：%d\n", median(b, num1), qcj(median(b, num1), boy[5], 1));
			break;
		}
		case 7:
		{
			for (j = 0; j < num; j++)
			{
				if (strcmp(a[j].sex, "男") == 0)
				{
					b[j] = a[j].pu_su;
				}
			}
			printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num1), qcj(mean(b, num1), boy[6], 0));
			printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num1), qcj(median(b, num1), boy[6], 0));
			break;
		}
		case 8:
		{
			for (k = 0; k < num; k++)
			{
				b[k] = a[k].total;
			}
			printf("平均数为：%.2f  \n", mean(b, num1));
			printf("中位数为：%.2f  \n", median(b, num1));
			break;
		}
		default:printf("无效数据，请重新输入！");
		}
	}
	else
		if (sex == 'B')
		{
			printf("1.BMI  2.肺活量  3.短跑  4.跳远  5.体前屈  6.长跑  7.仰卧起坐  8.总成绩\n");
			printf("请选择你要查看数据的项目：");
			scanf_s("%d", &i);
			switch (i)
			{
			case 1:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].BMI;
					}
				}
				num2 = cnt;
				temp = mean(b, num2);
				p = median(b, num2);
				if (temp < girl[0][0] || temp>girl[0][1] && temp < girl[0][2]) s1 = 80;
				else if (temp > girl[0][0] && temp < girl[0][1]) s1 = 100;
				else if (temp > girl[0][2]) s1 = 60;
				if (p < girl[0][0] || p>girl[0][1] && p < girl[0][2]) s2 = 80;
				else if (p > girl[0][0] && p < girl[0][1]) s2 = 100;
				else if (p > girl[0][2]) s2 = 60;
				printf("平均数为：%.2f  对应的成绩为：%d\n", temp, s1);
				printf("中位数为：%.2f  对应的成绩为：%d\n", p, s2);
				break;
			}
			case 2:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].lc;
					}
				}
				num2 = cnt;
				printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num2), qcj(mean(b, num2), girl[1], 0));
				printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num2), qcj(median(b, num2), girl[1], 0));
				break;
			}
			case 3:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].dash;
					}
				}
				num2 = cnt;
				printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num2), qcj(mean(b, num2), girl[2], 1));
				printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num2), qcj(median(b, num2), girl[2], 1));
				break;
			}
			case 4:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].jump;
					}
				}
				num2 = cnt;
				printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num2), qcj(mean(b, num2), girl[3], 0));
				printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num2), qcj(median(b, num2), girl[3], 0));
				break;
			}
			case 5:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].sr;
					}
				}
				num2 = cnt;
				printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num2), qcj(mean(b, num2), girl[4], 0));
				printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num2), qcj(median(b, num2), girl[4], 0));
				break;
			}
			case 6:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].dis_race;
					}
				}
				num2 = cnt;
				printf("平均数为：%.2f  对应的成绩为：%d\n", mean(b, num2), qcj(mean(b, num2), girl[5], 1));
				printf("中位数为：%.2f  对应的成绩为：%d\n", median(b, num2), qcj(median(b, num2), girl[5], 1));
				break;
			}
			case 7:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].pu_su;
					}
				}
				num2 = cnt;
				printf("平均数为：%.1f  对应的成绩为：%d\n", mean(b, num2), qcj(mean(b, num2), girl[6], 0));
				printf("中位数为：%.1f  对应的成绩为：%d\n", median(b, num2), qcj(median(b, num2), girl[6], 0));
				break;
			}
			case 8:
			{
				int cnt = 0;
				for (j = 0; j < num; j++)
				{
					if (strcmp(a[j].sex, "女") == 0)
					{
						b[cnt++] = a[j].total;
					}
				}
				num2 = cnt;
				printf("平均数为：%.1f  \n", mean(b, num2));
				printf("中位数为：%.1f  \n", median(b, num2));
				break;
			}
			default:printf("无效数据，请重新输入！");
			}
		}
		else printf("无效数据，请重新输入！");
}
float mean(float number[], int s)
{
	int i;
	float sum = 0, avg;
	for (i = 0; i < s; i++)
	{
		sum += number[i];
	}
	avg = sum / s;
	return avg;
}
float median(float number[], int s)
{
	int i, k;
	float temp = 0, z = 0;
	for (k = 0; k < s; k++)
	{
		for (i = 0; i < s - k - 1; i++)
		{
			if (number[i] > number[i + 1])
			{
				temp = number[i];
				number[i] = number[i + 1];
				number[i + 1] = temp;
			}
		}
	}
	if (s % 2 == 1) { return(number[s / 2]); }
	else
	{
		float a = number[s / 2];
		float b = number[s / 2 - 1];
		z = (a + b) / 2.0;
		return(z);
	}
}
