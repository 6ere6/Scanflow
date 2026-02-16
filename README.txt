# ScanFlow Network Utility

CLI C# (.NET) qui simplifie Nmap : profils prêts à l'emploi, suivi temps réel, historique rejouable et exports structurés (CSV/JSON).

## Fonctionnalités clés
- Profils de scan (ping sweep, full TCP, NSE ciblés)
- Validation des entrées (IP, CIDR, ports) + dry-run
- Suivi temps réel, throttling configurable
- Historisation, rejoue, filtres hôte/port/service
- Exports txt

## Prérequis
- Windows ou Linux avec .NET 8 SDK
- Nmap installé

## Installation
```bash
# Cloner
git clone https://github.com/6ere6/scanflow.git
cd scanflow

# Restaurer & build
 dotnet restore
 dotnet build -c Release

# Binaire prêt
 ./bin/Release/net8.0/scanflow.exe --help
```

## Usage rapide
```bash
# Découverte rapide (ping sweep)
scanflow preset quick-sweep --targets 192.168.1.0/24

# Scan complet TCP avec détection de versions
scanflow preset full-tcp --targets hosts.txt --rate 2000

# Dry-run pour vérifier la commande générée
scanflow preset full-tcp --targets 10.0.0.0/24 --dry-run
```

## Exemples avancés
```bash
# Scan custom avec ports spécifiques et scripts NSE vuln
scanflow custom --targets 192.168.1.42 --ports 22,80,443 --nse vuln

# Export structuré
scanflow preset quick-sweep --targets 10.0.0.0/24 --out results.csv --format csv

# Rejouer un scan depuis l'historique
scanflow history run --id 12
```

## Structure des sorties
- `stdout` : progression + résultats filtrés
- `logs/` : traces horodatées
- Exports : TXT


