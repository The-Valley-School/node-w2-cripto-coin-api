# Workshop 2 - API de Criptomonedas

Ya que están tan de moda las Criptomonedas, vamos a hacer una API para almacenar información sobre ellas.

**PASO 1**

Crea un nuevo proyecto en blanco en Github y recuerda instalar y configurar las siguientes librerías:

- Express
- Mongoose
- Dotenv
- Prettier
- Husky
- Eslint

**PASO 2**

Crea una base de datos en Mongo Atlas para almacenar tu información de criptomonedas:

![Untitled](/assets/Untitled.png)

Crea un fichero db.js para conectarte a tu base de datos y configura correctamente la conexión indicando los datos en un fichero privado .env

**PASO 3**

Crea un seed para rellenar de datos tu colección de cryptos

Te dejamos por aquí unos datos para que puedas precargar en la BBDD:

```jsx
const cryptoList = [
  { name: "Bitcoin", price: 57329.99, marketCap: 1077962308762, created_at: "2009-01-03T18:15:05.000Z" },
  { name: "Ethereum", price: 2230.16, marketCap: 258082329474, created_at: "2015-07-30T01:26:13.000Z" },
  { name: "Binance Coin", price: 549.54, marketCap: 84853731506, created_at: "2017-07-25T04:44:59.000Z" },
  { name: "Cardano", price: 1.28, marketCap: 40908813290, created_at: "2017-10-01T21:44:29.000Z" },
  { name: "Tether", price: 1.0, marketCap: 41409618000, created_at: "2014-11-20T06:36:20.000Z" },
  { name: "XRP", price: 1.68, marketCap: 76737229287, created_at: "2013-04-18T16:58:29.000Z" },
  { name: "Solana", price: 41.43, marketCap: 11603455490, created_at: "2020-03-18T20:22:23.000Z" },
  { name: "Polkadot", price: 41.85, marketCap: 40472684787, created_at: "2020-05-26T19:22:08.000Z" },
  { name: "Dogecoin", price: 0.34, marketCap: 44977516251, created_at: "2013-12-06T22:31:21.000Z" },
  { name: "USD Coin", price: 1.0, marketCap: 15732336636, created_at: "2018-09-26T23:11:46.000Z" },
  { name: "Aave", price: 457.81, marketCap: 5947881051, created_at: "2020-12-16T13:45:37.000Z" },
  { name: "Chainlink", price: 38.64, marketCap: 16989923434, created_at: "2017-09-20T19:44:14.000Z" },
  { name: "Bitcoin Cash", price: 1012.16, marketCap: 19004593616, created_at: "2017-07-23T23:27:51.000Z" },
  { name: "Litecoin", price: 287.87, marketCap: 19614490277, created_at: "2011-10-08T02:26:17.000Z" },
  { name: "Uniswap", price: 31.97, marketCap: 16650903753, created_at: "2020-09-17T17:25:40.000Z" },
  { name: "Theta Network", price: 11.12, marketCap: 11118649159, created_at: "2018-01-08T15:58:25.000Z" },
  { name: "Dent", price: 0.008624, marketCap: 932525678, created_at: "2017-07-12T14:50:00.000Z" },
  { name: "Chiliz", price: 0.4997, marketCap: 3091737381, created_at: "2018-06-02T20:17:59.000Z" },
  { name: "Fantom", price: 1.11, marketCap: 3121563451, created_at: "2018-06-02T20:17:59.000Z" },
  { name: "Harmony", price: 0.2069, marketCap: 1745227461, created_at: "2019-03-14T01:41:31.000Z" },
  { name: "BitTorrent", price: 0.002132, marketCap: 1696751105, created_at: "2019-01-28T09:36:27.000Z" },
  { name: "Flow", price: 17.89, marketCap: 1681560903, created_at: "2020-06-25T04:29:30.000Z" },
  { name: "Celsius", price: 5.01, marketCap: 1435799031, created_at: "2018-03-09T21:01:43.000Z" },
  { name: "Curve DAO Token", price: 2.12, marketCap: 1423039242, created_at: "2020-01-21T18:09:02.000Z" },
  { name: "Near", price: 5.71, marketCap: 1415588328, created_at: "2019-04-24T07:16:01.000Z" },
  { name: "Helium", price: 44.95, marketCap: 1381900023, created_at: "2019-06-28T18:15:27.000Z" },
];
```

Como ves vamos a trabajar con los siguientes datos:

- Nombre
- Precio
- Valor total de mercado
- Fecha de creación

**PASO 4**

Genera un CRUD completo para manejar las monedas con el API, tendremos:

GET /crypto que nos devolverá la lista de monedas, debe estar paginado con los parámetros page y limit:

![Untitled](/assets/Untitled%201.png)

GET /crypto/id que nos devolverá la info de una moneda:

![Untitled](/assets/Untitled%202.png)

POST /crypto que nos permitirá dar de alta una nueva moneda

![Untitled](/assets/Untitled%203.png)

PUT /crypto/id que nos permitirá editar una moneda

![Untitled](/assets/Untitled%204.png)

DELETE /crypto/id que nos permitirá borrar una moneda

![Untitled](/assets/Untitled%205.png)

**PASO 5**

Ahora debes crear algunos endpoints custom:

GET /crypto/name/nombre que nos permitirá buscar una moneda por nombre:

![Untitled](/assets/Untitled%206.png)

GET /crypto/csv que devolverá la lista de cryptomonedas pero en CSV

![Untitled](/assets/Untitled%207.png)

GET /crypto/sorted-by-marketcap?order=desc que devolverá las monedas ordenadas por valor de mercado. El orden puede ser ascendente (asc) o descendente (desc):

![Untitled](/assets/Untitled%208.png)

GET /crypto/sorted-by-date?order=asc que devolverá las monedas ordenadas por fechas de creación. También puede ser ascendente (asc) o descendente (dec):

![Untitled](/assets/Untitled%209.png)

GET /crypto/price-range?min=10&max=1000 que devolverá las monedas que se encuentren en el rango de precio que hemos indicado en los parámetros:

![Untitled](/assets/Untitled%2010.png)

DELETE /crypto/reset que ejecutará el seed de monedas de forma “remota” para no tener que ejecutarlo en consola. Como el seed, deberá borrar todas las monedas e insertar las monedas de ejemplo. Al final devolverá la lista de las monedas:

![Untitled](/assets/Untitled%2011.png)

**PASO 6**

Genera una colección de Postman para documentar tu API y recuerda subirla al repo donde tengas el código

Happy hacking!
