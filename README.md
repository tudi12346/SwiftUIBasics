# SwiftUIBasics

## Intro
Cele mai basic basics:
	https://developer.apple.com/tutorials/swiftui (skip lejer, totusi daca o sa mai dezvolt lista e un entry point bun)

Daca nu sunteti destul de familiarizati cu **trailing closures**, puteti cauta materiale in plus. Eu consider explicatia asta destul de ok
https://www.hackingwithswift.com/example-code/language/what-is-trailing-closure-syntax 

## Componente de baza 
- destul de straightforward, singura chestie de mentionat este legata de constructori, parametrii default pot fi omisi(asta pentru a tine codul curat):
  ```ZStack( alignment: center ) {} ```
este acelasi lucru cu 
  ```ZStack {} ```
	
  Pentru butoane, varianta a doua mi se pare mai clean:
<img width="641" alt="Constants HowHalenkorks showButtonText)" src="https://user-images.githubusercontent.com/56347575/162228956-48083cb1-fc6d-41ac-b9bd-7d7576d832fa.png">

<img width="334" alt="} label {" src="https://user-images.githubusercontent.com/56347575/162229049-f206421f-80c1-46df-99bf-68d36bc9738f.png">

(Aici e doar OCD 😂🤓)
Bonus: pentru management view-uri folosind stack uri 
	https://swdevnotes.com/swift/2021/layout-stacks-swiftui/ 

- pentru UI repetitiv cleanest way(parerea mea) sunt **view modifierii**. 

Exemplu:
Definesti un ViewModifier cu schimbarile pe care vrei sa le faci .

<img width="869" alt="Screenshot 2022-04-07 at 16 36 58" src="https://user-images.githubusercontent.com/56347575/162230557-88fa0f3f-0538-4b40-8554-ae4c1b1e6577.png">

Apoi definesti o functie care o sa aplice modifier-ul pe tipul de view pentru care l-ai facut. In exemplu este am extins View pentru a putea aplica modifier-ul pe orice tip de view

<img width="789" alt="extension Vies" src="https://user-images.githubusercontent.com/56347575/162230705-7eb850a2-d821-478b-832b-68a0adca2fc0.png">

Exemplu aplicare pe un Text()

<img width="678" alt="AnyView(CompleteProfileView())," src="https://user-images.githubusercontent.com/56347575/162230775-57458ef2-ba67-425e-ac10-92318534cc1b.png">


Mai departe pentru chestii specifice cititi voi ce modifieri default puteti folosi/inlantui. 

Keep in mind: CONTEAZA **ORDINEA** IN CARE SUNT SCRISI

Useful struct : GeometryReader
	

