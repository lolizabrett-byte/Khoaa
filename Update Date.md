#include <stdio.h>

typedef struct{
    int day;
    int month;
    int year;
}dmy;

int upgrade_date(dmy *a){
    if(a->month==1){
        if(a->day+1>31){
            a->day=1;
            a->month++;
        }
        else{(a->day)++;}
    }
    else if(a->month==2){
        if(a->day==28&&(a->year%4==0&&a->year%100!=0)||(a->year%400==0)){
            a->day=29;
        }
        else if(a->day>=28){
            a->day=1;
            a->month++;
        }
        else{(a->day)++;}
    }
    else{
        if(a->month%2==0){
            if(a->day+1>31){
            a->day=1;
            a->month++;
        }
        else{(a->day)++;}
        }
        else{
            if(a->day+1>30){
            a->day=1;
            a->month++;
        }
        else{(a->day)++;}
        }
    }
}

void input_date(dmy *a){
    printf("Nhap ngay: ");
    scanf("%d",&a->day);
    printf("\n");
    printf("Nhap thang: ");
    scanf("%d",&a->month);
    printf("\n");
    printf("Nhap nam: ");
    scanf("%d",&a->year);
    printf("\n");
}

void print_date(dmy a){
    printf("Ngay %d Thang %d Nam %d \n",a.day,a.month,a.year );
}

int main(){
    dmy a;
    input_date(&a);
    printf("Ngay thang nam nhap vao la: \n");
    print_date(a);
    upgrade_date(&a);
    if(a.month>12){
        a.month=1;
        a.year++;
    }
    printf("Ngay thang nam tiep theo la: \n");
    print_date(a);
}

