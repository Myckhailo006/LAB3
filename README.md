# LAB3[LP nr 3 KULEV.docx](https://github.com/user-attachments/files/24165671/LP.nr.3.KULEV.docx)
   	  
Lucrare practică nr. 3
la disciplina programarea calculatoarelor

Теmа: Prelucrarea tablourilor unidimensionale in limbajul C
Scopul lucrării: Studierea posibilităţilor şi mijloacelor limbajului C pentru programarea algoritmilor de prelucrare a tablourilor bidimensionale. Sarcină (cоnform variantelor): Pentru tabloul bidimensional dat din n linii şi m coloane:

Varianta 6. Să se calculeze numărul de minimuri locale ale tabloului. Un element al tabloului este minim local, dacă este strict mai mic decât toţi vecinii săi.
Fig 1.1
<img width="941" height="1022" alt="image" src="https://github.com/user-attachments/assets/ab0c7219-d20a-4ab3-8469-07ec2fc7f69e" />
Fig 1.2
<img width="941" height="981" alt="image" src="https://github.com/user-attachments/assets/ffe703cf-95b2-4056-b2de-48f804fff30b" />
Fig 1.3
<img width="695" height="555" alt="image" src="https://github.com/user-attachments/assets/a39f689c-2d16-48dc-a5da-a98f7b32f3d9" />
#include <stdio.h>

int main(void) {
    int n, m;
    scanf("%d %d", &n, &m);

    int a[100][100]; 

    
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            scanf("%d", &a[i][j]);
        }
    }

    int count = 0; 

    
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {

            int is_min = 1;  
            int x = a[i][j]; 

            
            for (int di = -1; di <= 1; di++) {
                for (int dj = -1; dj <= 1; dj++) {

                   
                    if (di == 0 && dj == 0) continue;

                    int ni = i + di; 
                    int nj = j + dj; 

                   
                    if (ni >= 0 && ni < n && nj >= 0 && nj < m) {

                       
                        if (a[ni][nj] <= x) {
                            is_min = 0;
                            break;
                        }
                    }
                }
                if (!is_min) break;
            }

            if (is_min) {
                count++;
            }
        }
    }

    printf("%d\n", count);
    return 0;
}



