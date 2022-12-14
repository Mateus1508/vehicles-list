# list-cars-front

## Como iniciar a aplicação na máquina ?

O projeto foi criado utilizando **Vite**. para iniciar deve digitar os seguintes comandos no terminal.

`` npm install ``
<br>
`` npm run dev ``

---

Foram utilizadas as seguintes estruturas de pastas
![image](https://user-images.githubusercontent.com/81775179/199745021-eed41824-58f8-47dc-93d3-f29713b32809.png)

O componente para a listagem de veículos está como **ListVehicle**
![image](https://user-images.githubusercontent.com/81775179/199747565-416aac2a-d3a4-4113-817c-0fee57a032d7.png)

---

## ListVehicle

Foi utilizado um **useEffect** para realizar o get na api e um **useState** para salvar os dados da API, como pode ser visto abaixo:

```
const [cars, setCars] = useState([]);

    useEffect(() => {
      api
          .get("")
          .then((item) => {
            setCars(item.data);
          })
          .catch((err) => {
            console.error("ops! ocorreu o erro " + err);
          })
    },[]);
```

---

Utilizei o **map** para retornar os dados como uma lista:

```
 {cars.map((item,index) => (
              <ul>
                <h4>Veículo {index + 1}</h4>
                <li>Marca: {item.marca_nome}</li>
                <li>Modelo: {item.nome_modelo}</li>
                <li>Ano: {item.ano}</li>
                <li>Combustível: {item.combustivel}</li>
                <li>Quantidade de portas: {item.num_portas}</li>
                <li>Valor Fipe: {item.valor_fipe}</li>
                <li>Cor: {item.cor}</li>
              </ul>
            ))}
```
## Home

Para os veículos antigos
``` 
    const oldVehicles = cars.filter(item => item.ano >= 2005);
```

---
Para os veículos em promoção
```
    const cheapVehicles = cars.sort((a,b) => {
      if(a.valor_fipe < b.valor_fipe) {
        return -1;
      } else {
        return true;
      }
});
    const resultCheapVehicles = cheapVehicles.slice(0,3);
```
---
Para os novos veículos
```
    const newVehicles = cars.sort((a,b) => {
      if(a.timestamp_cadastro > b.timestamp_cadastro) {
        return -1;
      } else {
        return true;
      }
    });
    const resultNewVehicles = newVehicles.slice(0,5);
```






