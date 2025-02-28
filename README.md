# Prima aplicație Docker

# Scop
Aceasta lucrare de laborator familiarizează cu elementele de bază ale containerizării și pregătește spațiul de lucru pentru următoarele lucrări de laborator.

# Sarcina

Instalarea Docker Desktop și verificarea funcționării acestuia.

# Executare 

1.Am creat un repositoriu nou pe GitHub cu numele containers02 
2.am clonat acest repositoriu intr-un folder Cvlab3 cu ajutorul comenzii git clone "url-ul catre repositoriu"
3.In directorul containers02 creem fișierul Dockerfile cu următorul conținut:

FROM debian:latest

COPY ./site/ /var/www/html/

CMD ["sh", "-c", "echo hello from $HOSTNAME"]

![image](https://github.com/user-attachments/assets/f9aa7ae2-7b53-45a2-9b9f-9359ff691a31)

tot aici facem director nou site cu fisierul index.html cu continut arbitrar(am lasat site gol)

![image](https://github.com/user-attachments/assets/8270046c-e3bf-4a8f-8314-eb9a1dca3be4)

4.Testare 
In terminal executam comanda docker build -t containers02 . (Astfel cream imaginiea)

![image](https://github.com/user-attachments/assets/634ec4a5-1bbf-4aaa-834f-cab1245109bb)

Crearea imaginii a durat 20.9 s (Timpul crearii poate varia caci laptopul nu era conectat la o sursa de alimentare => performanta scade)

Executam comanda pentru pornirea containerului: docker run --name containers02 containers02
Am obtinut afisarea in consola al urmatorului continut hello from a65298f5cd7b unde a65298f5cd7b este numele hostului 

![image](https://github.com/user-attachments/assets/ed1116bd-7bd1-484b-8d96-dea81c1daef6)

Ștergem containerul și il pornim din nou, executând comenzile:

docker rm containers02
docker run -ti --name containers02 containers02 bash

![image](https://github.com/user-attachments/assets/70c41373-6d67-42c8-bb2c-80eb5e9732ec)

In fereastra deschisa executam comenzile:

cd /var/www/html/
ls -l

si inchidem fereastra cu ajutorul comenzii exit

Ne apare ca fisierele listate in acest director ocupa un volum de 4KB(aceasta observam in afisarea la total 4)
-rwxr-xr-x → Permisiuni ale fișierului:

- Este un fișier obișnuit (nu director d, nu link l).
rwx Proprietarul (root) are drepturi de citire (r), scriere (w) și execuție (x).
r-x Grupul (root) are drepturi de citire și execuție, dar nu de scriere.
r-x Alți utilizatori au aceleași drepturi ca și grupul (citire și execuție).
1 Numărul de legături (hard links) către fișier.

root root Proprietarul și grupul care dețin fișierul (root este atât utilizatorul, cât și grupul).

215 Dimensiunea fișierului în bytes (215 bytes).

Feb 28 06:44 Data și ora ultimei modificări (28 februarie, ora 06:44).

index.html Numele fișierului.

![image](https://github.com/user-attachments/assets/c24d7ec0-a6da-4de0-bfbf-dcb6faf1a419)
