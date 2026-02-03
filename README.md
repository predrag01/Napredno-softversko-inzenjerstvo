# Napredno-softversko-inzenjerstvo

# Implementacija mikroservisnog sistema za obradu medicinskih podataka putem Apache Kafka poruka (PatientSupport)

## Opis
PatientSupport je web aplikacija koja demonstrira primenu event-driven mikroservisne arhitekture u obradi medicinskih podataka u realnom vremenu. Sistem prikuplja (simulira) očitavanja vitalnih parametara, obrađuje ih asinhrono i omogućava reakcije kao što su analiza stanja, obaveštavanje i zakazivanje termina. Iako je domen zdravstvo, fokus projekta je arhitektura i komunikacija mikroservisa zasnovana na događajima.  
Korišćene tehnologije uključuju .NET servise, React klijentsku aplikaciju i posrednika događaja (Kafka) radi skalabilne i pouzdane asinhrone komunikacije. 

## Tehnologije
- .NET (ASP.NET Web API)  
- React (Vite)  
- SignalR (real-time obaveštavanje)  
- Apache Kafka (event-driven komunikacija)  
- Microsoft SQL Server (baze po servisima)  
- Redis (keširanje / brži pristup podacima)  
- Docker  

## Pokretanje projekta

### Preduslovi
- **Docker Desktop** (Docker + Docker Compose)
- **Node.js + npm** (za build/pokretanje frontenda)  

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
