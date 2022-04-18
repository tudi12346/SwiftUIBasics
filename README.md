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

- pentru UI repetitiv cleanest way(parerea mea) sunt **view modifierii** (strict pentru modificarea aspectului). 

Exemplu:
Definesti un ViewModifier cu schimbarile pe care vrei sa le faci .

<img width="869" alt="Screenshot 2022-04-07 at 16 36 58" src="https://user-images.githubusercontent.com/56347575/162230557-88fa0f3f-0538-4b40-8554-ae4c1b1e6577.png">

Apoi definesti o functie care o sa aplice modifier-ul pe tipul de view pentru care l-ai facut. In exemplu am extins View pentru a putea aplica modifier-ul pe orice tip de view

<img width="789" alt="extension Vies" src="https://user-images.githubusercontent.com/56347575/162230705-7eb850a2-d821-478b-832b-68a0adca2fc0.png">

Exemplu aplicare pe un Text()

<img width="678" alt="AnyView(CompleteProfileView())," src="https://user-images.githubusercontent.com/56347575/162230775-57458ef2-ba67-425e-ac10-92318534cc1b.png">

## Fonturi 

Cleanest way (again parerea mea), dupa ce se importa fonturile in aplicatie si le am [inregistrat in info.plist](https://developer.apple.com/documentation/uikit/text_display_and_fonts/adding_a_custom_font_to_your_app) putem extinde Font pentru a usura folosirea fonturilor custom

<img width="597" alt="Screenshot 2022-04-07 at 18 20 44" src="https://user-images.githubusercontent.com/56347575/162234307-c42c67a1-b7e4-4c34-9c10-252c382f078b.png">

Folosire:

<img width="321" alt="Screenshot 2022-04-07 at 18 26 50" src="https://user-images.githubusercontent.com/56347575/162235631-3b15ec68-6c1e-4867-9ef2-b6f0a8fdafdb.png">


Keep in mind: CONTEAZA **ORDINEA** IN CARE SUNT SCRISI

Useful struct : GeometryReader

Basics: 

https://www.hackingwithswift.com/quick-start/swiftui/how-to-provide-relative-sizes-using-geometryreader

Advanced: 

https://www.hackingwithswift.com/books/ios-swiftui/understanding-frames-and-coordinates-inside-geometryreader
	

## Passing data between views + Observing changes

INTRO: [Value types vs Reference types](https://www.codementor.io/blog/value-vs-reference-6fm8x0syje) (este si o intrebare comuna la interviuri) 

Property wrappers

@State -> muta proprietatea intr-un shared storage manageuit de SwiftUI, pentru a pastra informatia stocata( cand se distruge / construieste din nou view-ul) Schimbarile acestei proprietati marcata ca @State updateaza view ul. Poate fi trimis si unui child view, iar acesta o sa raspunda si el la schimbari. Totusi, Child View ul nu poate modifica valoarea.

[@Binding](https://developer.apple.com/documentation/swiftui/binding) -> Se foloseste pentru a trimite informatia de la o proprietate State catre un Child View, dar in varianta asta Child View ul poate modifica valoarea. Ca sa trimiti o proprietate State dintr-un View ca si binding intr-un alt view: prefix cu $ la numele variabilei(accesezi projectedValue). 

Exemplu Binding si State foarte bun in [documentatia Apple](https://developer.apple.com/documentation/swiftui/state)

@StateObject si  @ObservedObject

Ambii wrapperi sunt folositi pentru a observa obiecte de tip ObservableObject. Pentru a notifica UI-ul despre schimbarile care se fac la nivelul obiectelor, proprietatile lor (care influenteaza UI-ul) trebuie marcate cu @Published. 

<img width="500" alt="Screenshot 2022-04-07 at 18 26 50" src="https://user-images.githubusercontent.com/56347575/162695857-7d28ee2b-c949-458e-a702-9bc235cd3dc6.png">

Diferentele si similaritatile dintre cei 2 wrapperi sunt prezentate foarte bine in articolul [asta](https://medium.com/geekculture/swiftui-stateobject-and-observedobject-c6640c1bd2fd).

@EnvironmentObject -> Este folosit pentru a distribui obiecte intre mai multe view-uri (fara sa mai fie nevoie sa scriem binding-uri). Ar trebui folosit cand obiectul este accesat/observat de un nr mare de view-uri. Mai multe detalii si exemplu [aici](https://www.hackingwithswift.com/quick-start/swiftui/how-to-use-environmentobject-to-share-data-between-views).

## Very useful resource for animations

https://github.com/amosgyamfi/swiftui-animation-library

## Managing loading states

https://www.swiftbysundell.com/articles/handling-loading-states-in-swiftui/
