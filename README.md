#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <ctype.h>
typedef struct
{
    char hoten[30];
    unsigned int namsinh;
    float hsl;
}CB;
struct node
{
    CB data;
    struct node *next;
};
typedef struct node *LinkList;
void Taodslknguoc(LinkList &pdau)
{
    LinkList p;
    pdau = NULL;
    do
    {
        p = (LinkList)malloc(sizeof(struct node));
        printf("Moi nhap ho ten can bo: ");
        fflush(stdin);
        gets(p->data.hoten);
        printf("Moi nhap nam sinh: ");
        scanf("%d", &p->data.namsinh);
        printf("Moi nhap he so luong: ");
        scanf("%f", &p->data.hsl);
        p -> next = pdau;
        pdau = p;
        printf("Ban co muon nhap them khong?C/K\n");
    }while(toupper (getch()) != 'K');
}
void Taodslkthuan(LinkList &pdau)
{
    LinkList p, pcuoi;
    pdau = NULL;
    do
    {
        p = (LinkList)malloc(sizeof(struct node));
        printf("Moi nhap ho ten can bo: ");
        fflush(stdin);
        gets(p->data.hoten);
        printf("Moi nhap nam sinh: ");
        scanf("%d", &p->data.namsinh);
        printf("Moi nhap he so luong: ");
        scanf("%f", &p->data.hsl);
        if(pdau == NULL)
            pdau = p;
        else
            pcuoi -> next = p;
        pcuoi = p;
        pcuoi -> next = NULL;
        printf("Ban co muon nhap them khong?C/K\n");
    }while(toupper (getch()) != 'K');
}
void Inds(LinkList pdau)
{
    LinkList p;
    int i = 0;
    printf("\t\tDANH SACH CAN BO\n\n");
    printf("| STT |           HO VA TEN          | NAM SINH | HE SO LUONG |\n");
    p = pdau;
    i = 1;
    while(p != NULL)
    {

        printf("|%5d|%-30s|%10d|%13.1f|\n", i++, p->data.hoten, p->data.namsinh, p->data.hsl);
        p = p -> next;
    }
}
void chendau(LinkList &pdau, CB x)
{
    LinkList p, pmoi;
    pmoi = (LinkList)malloc(sizeof(struct node));
    pmoi -> data = x;
    pmoi -> next = pdau;
    pdau = pmoi;
}
void chencuoi(LinkList &pdau, CB x)
{
    LinkList p, pmoi;
    pmoi = (LinkList)malloc(sizeof(struct node));
    pmoi -> data = x;
    p = pdau;
    while(p->next != NULL)
    {
        p = p -> next;
    }
    pmoi -> next = p -> next;
    p -> next = p;
}
main()
{
    LinkList pdau;
    int chon;
    CB x;
    do
    {
        printf("\n\t\tMENU\n\n");
        printf("1. Tao nguoc.\n");
        printf("2. Tao thuan.\n");
        printf("3. In danh sach.\n");
        printf("4. Chen dau.\n");
        printf("5. Chen cuoi.\n");
        printf("Muon thoat nhan 20.\n");
        printf("Moi ban chon so 1 -> 3.\n");
        scanf("%d", &chon);
        switch(chon)
        {
            case 1: Taodslknguoc(pdau); break;
            case 2: Taodslkthuan(pdau); break;
            case 3: Inds(pdau); break;
            case 4:
                  {
                    printf("Moi nhap ho ten can bo: ");
                    fflush(stdin);
                    gets(x.hoten);
                    printf("Moi nhap nam sinh: ");
                    scanf("%d", &x.namsinh);
                    printf("Moi nhap he so luong: ");
                    scanf("%f", &x.hsl);
                    chendau(pdau, x);
                  }; break;
            case 5:
                  {
                    printf("Moi nhap ho ten can bo: ");
                    fflush(stdin);
                    gets(x.hoten);
                    printf("Moi nhap nam sinh: ");
                    scanf("%d", &x.namsinh);
                    printf("Moi nhap he so luong: ");
                    scanf("%f", &x.hsl);
                    chencuoi(pdau, x);
                  }; break;
        }
    }while(chon != 20);
}

