#uni 
ridefinire operatore di uscita:
`friend ostream& operator<<(ostream& os, const Classe&nome);` in .h
`ostream& operator<<(ostream& os, const Classe&nome) {...}` in .cpp
costruttore:
`Classe(parametri);` in .h
`Classe::Classe(parametri) {...}` in .cpp
distruttore:
`virtual ~Classe();` in .h
`Classe::~Classe() {...}` in .cpp
costruttore di copia:
`Classe(const Classe&daCopiare);` in .h
`Classe::Classe(const Classe&daCopiare) {...}` in .cpp
operatore + :
`friend Classe operator+(const Classe&nome1, const Classe&nome2);` in .h
`Classe operator+(const Classe &nome1, const Classe &nome2) {...}` in .cpp
operatore += :
`Classe& operator+=(const Classe&daAggiungere);` in .h
`Classe& Classe::operator+=(const Classe&daAggiungere) { ... return *this; }` in .cpp
operatore post incremento: 
`Classe operator++(int);` in .h (oggetto++; e non ++oggetto;)
`Classe Classe::operator++(int) {...}` in .cpp
operatore pre incremento:
`basta rimuovere int dai parametri`
operatore int() :
`operator int() const;` in .h
`Classe::operator int() const {...}` in .cpp