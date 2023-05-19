<script>
	const options = {
		method: 'GET',
		headers: {
			'X-RapidAPI-Key': '20ceffe9a3mshdb561d4c76a5dfbp1b1157jsn112e5dc50ba5',
			'X-RapidAPI-Host': 'weatherapi-com.p.rapidapi.com'
		}
	};

	const climaPromise = fetch ('https://weatherapi-com.p.rapidapi.com/current.json?q=Buenos%20Aires', options)
    .then((response)=> response.json())
    .then((response)=> {
        const {location, current} = response
        const {country, localtime, name} = location
        const {condition, humidity, feelslike_c, is_day, temp_c} = current
        const {code, text} = condition

        return {
        codigoCondicion : code,
        textoCondicion : text,
        ciudad: country,
        fecha: localtime,
        nombre: name,
        condicion: condition,
        humedad: humidity,
        esDia : is_day,
        sensacionTermica : feelslike_c,
        temperatura : temp_c
    }
    });
</script>

{#await climaPromise then clima}
    <h1>{clima.textoCondicion}</h1>
{/await}

<h1>Hola</h1>

<style>
	h1 {
		font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
			Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
	}
</style>
