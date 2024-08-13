This is the System Layer of the Pokemon DDBB, it contains the interface and implements of the HTTP methods for:
- Get All Pokemons in the DDBB "/api/pokemon"
- Get the Pokemon with specified ID "/api/pokemon/ID"
- Get the Pokemons with specified type "/api/pokemon/tipo?tipo=type"
- Get the Pokemons of specified generation "/api/pokemon/generacion?gen=generation"
- Get the Pokemon with the specified name "/api/pokemon/nombre?nombre=name"
- Update the "MainType" of the specified ID Pokemon "/api/pokemon/ID/tipo1?tipo1=MainType"
- Update the "SecondaryType" of the specified ID Pokemon "/api/pokemon/ID/tipo1?tipo2=SecondaryType"
- Update the "generation" of the specified ID Pokemon "/api/pokemon/ID/generacion?gen=generation"
- Create (Post) the Pokemon with the specified "name", "MainType" ("SecondaryType" and "Gen" are optional) "/api/pokemon?nombre=name&tipo1=MainType&tipo2=SecondaryType&gen=generation"
- Delete the Pokemon with the specified ID "/api/pokemon/ID"
- Train (Patch) the specified ID Pokemon with a numeric ammount of xp "/api/pokemon/ID/entrenar?xp=xp"
- Teach (Patch) the specified ID Pokemon the specified move "/api/pokemon/ID/aprender?mov=move"
- Forget (Patch) the specified ID Pokemon the move in the positional slot (mov1 - mov4)  "/api/pokemon/ID/olvidar?move"

The train Pokemon recalls the previously earned xp and sums the trained ammount so it sets the new total xp, calculating the and updating the level of the Pokemon
The teach Pokemon uses a Scather-Gather to validate un paralell if the Pokemon already knows the move that it's learning and throws an error if thats true. If not, a chain of Choice process will start, validating if the first move slot is not empty. If it fails, the next choice will validate the second move slot, and then the 3rd and 4th so the Pokemon will learn the move in the first empty slots. If the Pokemon already knows 4 moves, a payload will be returned asking to forget a move
