# Delilnica

Delilnica je spletna storitev za deljenje izsekov besedila in programske kode. Sestavljajo jo trije deli:

- Spletni vmesnik, ki uporablja Flask: <https://github.com/delilnica/ospredje>
- Aplikacijski vmesnik, ki uporablja FastAPI: <https://github.com/delilnica/zaledje>
- Generator identifikatorjev v obliki funkcije kot storitve <https://github.com/delilnica/idgen>

Vsi deli so kontejnerizirani. Zaledje in ospredje sta zlepljena z orodjem Docker Compose, *idgen* pa nadzira storitev *faasd* (OpenFaaS).

## Navodila za izgradnjo

Ta repozitorij je namenjen lažji (hkratni) vzpostavitvi vseh treh storitev, kar omogočajo podmoduli orodja git. Sprva jih je potrebno ustrezno inicializirati:

```
git clone https://github.com/delilnica/delilnica
cd delilnica
git submodule update --init
```

Sledi izgradnja kontejnerjev:

```
docker-compose build
```

V tej točki je potrebno zagnati *idgen*. [Navodila](https://github.com/delilnica/idgen) so v njegovem repozitoriju.

Če se vmes ni zalomilo, je potreben še poslednji ukaz:

```
docker-compose up
```

Ospredje bo prevezano na vrata 80, zaledje ostane na 8000, *idgen* pa na 8080.

