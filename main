#include <stdio.h>
#include <conio.h>
#include <windows.h>

void clrscr() { system("CLS"); }

void gotoxy(short x, short y) 
	{ COORD pos = {x, y};
	  SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), pos);
	}

void PBaslik()
    { clrscr();
      gotoxy(11, 1); printf("Menulu SED ile Dosyalama");
      gotoxy(44, 1); printf("Vers: 1.00");
	  gotoxy(66, 1); printf("RESUL TUZEN");
    }
void Pmenu ()
    { PBaslik();
      gotoxy(11, 5); printf("---_MENU_---");
      gotoxy(11, 6); printf("1. K. Yaz");
      gotoxy(11, 7); printf("2. K. AraBulGoster");
      gotoxy(11, 8); printf("3. K. Sil");
      gotoxy(11, 9); printf("4. K. Duzelt");
      gotoxy(11,10); printf("5. K. Listele");
      gotoxy(11,11); printf("0. CIKIS");
      gotoxy(11,15); printf("Bir Secenek Giriniz: ");
    }
void BilEkr ()
    { PBaslik();
      gotoxy( 5, 4); printf("---Ogrenci Bilgileri---");
      gotoxy( 5, 5); printf("Numara.......:");
      gotoxy( 5, 6); printf("Ad...........:");
      gotoxy( 5, 7); printf("Soyad........:");
      gotoxy( 5, 8); printf("Telefon......:");
      gotoxy( 5, 9); printf("Yas..........:");
    }
void BilGos (int nmr, char adi[15], char syd[15],char tlf[11], int yas)
    {
      gotoxy(22, 5); printf("%d" , nmr);
      gotoxy(22, 6); printf("%s" , adi);
      gotoxy(22, 7); printf("%s" , syd);
      gotoxy(22, 8); printf("%s" , tlf);
      gotoxy(22, 9); printf("%d" , yas);
    }
int main()
{
	FILE *OgrDos, *GecDos;
	struct KayTipi { int nmr;
			 			char adi[15];
			 			char syd[15];
						char tlf[11];
			 			int yas;
		       		} ODBlg;

	int Anmr, sec, bul=0;
Bsl:
	clrscr();
Menu:
	PBaslik();
	Pmenu();
Miste:
	gotoxy(33,15); scanf("%d",&sec);
	if (sec==0) goto Son;
	if (sec>5) { gotoxy(11,20); printf("Hatali Secim Yapildi, Tekrar Giriniz."); goto Miste; }
	if (sec==1) goto DkYaz;
	if (sec==2) goto DkOku;
	if (sec==3) goto DkSil;
	if (sec==4) goto DkDuz;
	if (sec==5) goto DkLst;
	goto Miste;
DkYaz:
	BilEkr();
	gotoxy(11,20); printf("Lutfen Bilgileri Giriniz...");
	gotoxy(20, 5); scanf("%d" , &ODBlg.nmr);
	gotoxy(20, 6); scanf("%s" , &ODBlg.adi);
	gotoxy(20, 7); scanf("%s" , &ODBlg.syd);
	gotoxy(20, 8); scanf("%s" , &ODBlg.tlf);
	gotoxy(20, 9); scanf("%d" , &ODBlg.yas);
	gotoxy(44, 4); printf("---Girilenler---");
	gotoxy(44, 5); printf("%d" , ODBlg.nmr);
	gotoxy(44, 6); printf("%s" , ODBlg.adi);
	gotoxy(44, 7); printf("%s" , ODBlg.syd);
	gotoxy(44, 8); printf("%s" , ODBlg.tlf);
	gotoxy(44, 9); printf("%d" , ODBlg.yas);
	OgrDos=fopen("ogr.dat","a");
	   fprintf(OgrDos,"\n%d %s %s %s %d",ODBlg.nmr,ODBlg.adi,ODBlg.syd,ODBlg.tlf,ODBlg.yas);
	fclose(OgrDos);
	gotoxy(11,21); printf("Kayit YAZILDI.");
	gotoxy(11,22); printf("Menuicin ENTER Tuslayiniz: "); getch();
DKYcik:
	goto Menu;
DkOku:
	PBaslik();
	gotoxy(11,11); printf("Aranan Kisinin NUMARASINI Giriniz: ");
	scanf("%d", &Anmr);
	if (Anmr==0) goto DKOcik;
	OgrDos=fopen("ogr.dat","r");
	bul=0;
	while (!feof(OgrDos))
	    { fscanf(OgrDos,"%d %s %s %s %d",&ODBlg.nmr,&ODBlg.adi,&ODBlg.syd,&ODBlg.tlf,&ODBlg.yas);
	      if (Anmr==ODBlg.nmr)
		{ bul=1;
		  BilEkr(); gotoxy(5,4); printf("---Okunan Bilgiler---");
		  BilGos (ODBlg.nmr,ODBlg.adi,ODBlg.syd,ODBlg.tlf,ODBlg.yas);
		}
	    }
	fclose(OgrDos);
	if (bul==0) {  gotoxy(11,20); printf("BULUNAMADI..."); }
	gotoxy(11,22);printf("Menu icin ENTER Tuslayiniz:"); getch();
DKOcik:
	goto Menu;
DkSil:
	PBaslik();
	gotoxy(11,11); printf("SiLiNECEK Kisinin NUMARASINI Giriniz: ");
	scanf("%d", &Anmr);
	if (Anmr==0) goto DKScik;
	OgrDos=fopen("ogr.dat","r"); GecDos=fopen("gecici.dat","w");
	bul=0;
	while (!feof(OgrDos))
	    { fscanf(OgrDos,"%d %s %s %s %d",&ODBlg.nmr,&ODBlg.adi,&ODBlg.syd,&ODBlg.tlf,&ODBlg.yas);
	      if (Anmr==ODBlg.nmr)
		{ bul=1;
		  BilEkr(); gotoxy(5,4); printf("---Silinecek Bilgiler---");
		  BilGos (ODBlg.nmr,ODBlg.adi,ODBlg.syd,ODBlg.tlf,ODBlg.yas);
		  gotoxy(22,20); printf("SiLiNDi.");
		}
	      else fprintf(GecDos,"\n%d %s %s %s %d",ODBlg.nmr,ODBlg.adi,ODBlg.syd,ODBlg.tlf,ODBlg.yas);
	    }
	fclose(OgrDos);	 fclose(GecDos);
	remove("ogr.dat");  rename("gecici.dat","ogr.dat");
	if (bul==0) { gotoxy(11,20); printf("BULUNAMADI..."); }
	gotoxy(11,22); printf("Menu icin ENTER Tuslayiniz:"); getch();
DKScik:
	goto Menu;
DkDuz:
	PBaslik();
	gotoxy(11,11); printf("DUZELTiLECEK Kisinin NUMARASINI Giriniz: ");
	scanf("%d", &Anmr);
	if (Anmr==0) goto DKDcik;
	OgrDos=fopen("ogr.dat","r");  GecDos=fopen("gecici.dat","w");
	bul=0;
	while (!feof(OgrDos))
	    { fscanf(OgrDos,"%d %s %s %s %d",&ODBlg.nmr,&ODBlg.adi,&ODBlg.syd,&ODBlg.tlf,&ODBlg.yas);
	      if (Anmr==ODBlg.nmr)
		{ bul=1;
		  BilEkr(); gotoxy(5,4); printf("---Okunan Bilgiler---");
		  BilGos (ODBlg.nmr,ODBlg.adi,ODBlg.syd,ODBlg.tlf,ODBlg.yas);
		  gotoxy(55, 4); printf("---Yenileri Giriniz---");
		  gotoxy(55, 5); scanf("%d" , &ODBlg.nmr);
		  gotoxy(55, 6); scanf("%s" , &ODBlg.adi);
		  gotoxy(55, 7); scanf("%s" , &ODBlg.syd);
		  gotoxy(55, 8); scanf("%s" , &ODBlg.tlf);
		  gotoxy(55, 9); scanf("%d" , &ODBlg.yas);
		  gotoxy(22,19); printf("DUZELTiLDi.");
		}
	      fprintf(GecDos,"\n%d %s %s %s %d",ODBlg.nmr,ODBlg.adi,ODBlg.syd,ODBlg.tlf,ODBlg.yas);
	    }
	fclose(OgrDos);	 fclose(GecDos);
	remove("ogr.dat");  rename("gecici.dat","ogr.dat");
	if (bul==0) { gotoxy(11,20); printf("BULUNAMADI..."); }
	gotoxy(11,22); printf("Menu icin ENTER Tuslayiniz:"); getch();
DKDcik:
	goto Menu;
DkLst:
      PBaslik();
      OgrDos=fopen("ogr.dat","r");
      while (!feof(OgrDos))
	  { fscanf(OgrDos,"%d %s %s %s %d",&ODBlg.nmr,&ODBlg.adi,&ODBlg.syd,&ODBlg.tlf,&ODBlg.yas);
	    BilEkr();
	    gotoxy(5,4); printf("---Okunan Bilgiler---");
	    BilGos (ODBlg.nmr,ODBlg.adi,ODBlg.syd,ODBlg.tlf,ODBlg.yas);
	    gotoxy(11,20); printf("SONRAKi Kayit icin ENTER Tuslayiniz: "); getch();
	  }
      fclose(OgrDos);
      gotoxy(11,22); printf("Menu icin ENTER Tuslayiniz: "); getch();
DKLcik:
	goto Menu;
Son:
	gotoxy(21,21); printf("Program SONLANDI, iyi Gunler...");
	return 0;
}
