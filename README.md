# Napredno-softversko-inzenjerstvo

# Implementacija mikroservisnog sistema za obradu medicinskih podataka putem Apache Kafka poruka (PatientSupport)

## Opis
PatientSupport je web aplikacija koja demonstrira primenu event-driven mikroservisne arhitekture u obradi medicinskih podataka u realnom vremenu. Sistem prikuplja (simulira) očitavanja vitalnih parametara, obrađuje ih asinhrono i omogućava reakcije kao što su analiza stanja, obaveštavanje i zakazivanje termina. Iako je domen zdravstvo, fokus projekta je arhitektura i komunikacija mikroservisa zasnovana na događajima.

## Tehnologije
- .NET (ASP.NET Web API)  
- React  
- SignalR  
- Apache Kafka (event-driven komunikacija)  
- Microsoft SQL Server  
- Redis
- Python
- Docker  

## Pokretanje projekta

### Preduslovi
- **Docker Desktop** (Docker + Docker Compose)
- **Node.js + npm** (za build/pokretanje frontenda)
- **- Python 3.x** (za pokretanje skripte koja simulira IoT uredjaje) 

### 1) Pokretanje backend servisa + infrastrukture (Kafka, SQL Server, Redis)
Pozicioniraj se u folder **PatientSupport** (gde se nalazi `docker-compose.yml`) i pokreni:

```bash
docker compose up --build
```

### **2) Build / pokretanje frontenda**

U folderu klijenta (PatientSupport/patientsupport.client) pokreni:

```bash
npm install
npm run dev
```
### **3) Pokretanje skipte koja simulira IoT uredjaje**

Aplikacija očekuje ulazne podatke (očitanja) koji se šalju u **Apache Kafka** topic **`reading-data`**.  
Da bi se generisala testna očitavanja, potrebno je pokrenuti Python skriptu koja simulira IoT uređaj i periodično šalje poruke na Kafka broker (`localhost:9092`).

### Preduslovi
- Python 3.x
- Instalirane biblioteke: `kafka-python`, `pytz`

Instalacija zavisnosti:

```bash
pip install kafka-python pytz
```

### Pokretanje skirpte
Pozicionirati se u folder _PatientSupport/PatientSuport.DeviceService_
Skripta prima dva argumenta:

--patient-id (ID pacijenta)

--patient-type (tip simulacije)

```bash
python main.py --patient-id 5 --patient-type Normal
```

**Dozvoljeni `--patient-type`:**
- Normal
- Hypertension
- HypertensionWithHighBPM
- Hypotension
- HypotensionWithLowBPM
- Arrhythmia
- Tachycardia
- Bradycardia
- Hypoxia
- Hyperthermia
- Hypothermia
- Diabetic

## Demo nalozi (Seed podaci)

Prilikom prvog pokretanja aplikacije baza se automatski popunjava testnim korisnicima.

### Administrator
- **Email:** admin@gmail.com  
- **Password:** admin123  

### Doktori
- **Email:** marko.petrovic@gmail.com  
  **Password:** doctor123  

- **Email:** ivana.jovanovic@gmail.com  
  **Password:** doctor123  

- **Email:** nenad.stankovic@gmail.com  
  **Password:** doctor123  
  *(nalog je inicijalno deaktiviran)*

### Pacijenti
Svi pacijenti koriste isti password.

- **Password:** patient123  

| Email |
|------|
| milan.ilic@gmail.com |
| ana.kovacevic@gmail.com |
| nikola.petrovic@gmail.com |
| jovana.stojanovic@gmail.com |
| marko.djordjevic@gmail.com |
| ivana.jankovic@gmail.com |
| stefan.nikolic@gmail.com |
| marija.milovanovic@gmail.com |
| aleksandar.radovanovic@gmail.com |
| katarina.tomic@gmail.com |

