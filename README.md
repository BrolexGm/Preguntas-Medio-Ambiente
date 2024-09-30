import discord
from discord.ext import commands

# Crea un bot con el prefijo "!"
intents = discord.Intents().all()
bot = commands.Bot(command_prefix="!", intents = intents)


# Define una lista de preguntas y respuestas sobre el medio ambiente
environment_facts = {
    "¿Qué es el cambio climático?": "El cambio climático es un cambio a largo plazo en los patrones climáticos, principalmente debido a la actividad humana como la quema de combustibles fósiles.",
    "¿Qué es la huella de carbono?": "La huella de carbono es la cantidad total de gases de efecto invernadero emitidos por las actividades humanas, generalmente expresada en toneladas de CO2.",
    "¿Cómo puedo reducir el uso de plástico?": "Puedes reducir el uso de plástico reutilizando bolsas, evitando productos de un solo uso y reciclando correctamente.",
    "¿Qué es el reciclaje?": "El reciclaje es el proceso de convertir residuos en nuevos productos para evitar el desperdicio de materiales útiles.",
    "¿Qué es la deforestación?": "La deforestación es la eliminación de árboles y bosques, a menudo para el uso de la tierra en agricultura o desarrollo urbano."
}

# Evento cuando el bot se conecta
@bot.event
async def on_ready():
    print(f'Bot conectado como {bot.user}')

# Comando para hacer preguntas sobre el medio ambiente
@bot.command()
async def pregunta(ctx, *, question: str):
    respuesta = environment_facts.get(question, "Lo siento, no tengo una respuesta para eso.")
    await ctx.send(respuesta)

# Ejecuta el bot
bot.run(#Token#)
