local TBLanguage = (function()
    local Localization = { locale = "en", bindings = {}, connections = {}, cache = {} }
    local catalog = {
        ["Amulet Building"] = { "Melhoria de amuletos", "Mejora de amuletos" },
        ["Hero Passives"] = { "Passivas de heróis", "Pasivas de héroes" },
        ["Shadow Passives"] = { "Passivas de sombras", "Pasivas de sombras" },
        ["Weapon Passives"] = { "Passivas de armas", "Pasivas de armas" },
        ["Weapon Passive Target"] = { "Arma para trocar a passiva", "Arma para cambiar la pasiva" },
        ["Auto Roll Weapon Passives"] = {
            "Girar passivas de arma automaticamente",
            "Girar pasivas de arma automáticamente",
        },
        ["Refresh Gacha Targets"] = { "Atualizar alvos de gacha", "Actualizar objetivos de gacha" },
        ["Select the weapon to reroll. Stop targets come from the game Manage menu."] = {
            "Selecione a arma. Os resultados para parar são definidos no menu Manage do jogo.",
            "Selecciona el arma. Los resultados para detenerse se configuran en el menú Manage del juego.",
        },
        ["Uses Weapon Passive Coins and native spin slots."] = {
            "Usa moedas de passiva de arma e os slots nativos.",
            "Usa monedas de pasiva de arma y los espacios nativos.",
        },
        ["Selection follows your native simultaneous spin limit."] = {
            "A seleção segue seu limite nativo de giros simultâneos.",
            "La selección sigue tu límite nativo de giros simultáneos.",
        },
        ["Auto Rank Up"] = { "Subir de rank automaticamente", "Subir de rango automáticamente" },
        ["Rank up / rebirth when energy is sufficient. Resets energy according to game rules."] = {
            "Sobe de rank quando há energia suficiente. Reinicia a energia conforme as regras do jogo.",
            "Sube de rango cuando hay energía suficiente. Reinicia la energía según las reglas del juego.",
        },
        ["Claim completed achievements automatically"] = {
            "Coleta conquistas concluídas automaticamente",
            "Recoge logros completados automáticamente",
        },
        ["Auto Claim Chests"] = { "Coletar baús automaticamente", "Recoger cofres automáticamente" },
        ["Claim eligible VIP, Premium and Group chests when ready"] = {
            "Coleta baús VIP, Premium e de grupo disponíveis",
            "Recoge cofres VIP, Premium y de grupo disponibles",
        },
        ["Auto Claim Daily Rewards"] = { "Coletar recompensas diárias", "Recoger recompensas diarias" },
        ["Claim daily rewards when playtime requirements are met"] = {
            "Coleta recompensas diárias ao cumprir o tempo necessário",
            "Recoge recompensas diarias al cumplir el tiempo necesario",
        },
        ["Auto Claim / Reset Hour Rewards"] = {
            "Coletar / reiniciar recompensas por hora",
            "Recoger / reiniciar recompensas por hora",
        },
        ["Claim available rewards; reset only after all are claimed and the timer allows it"] = {
            "Coleta recompensas disponíveis; reinicia após coletar todas e o tempo permitir",
            "Recoge recompensas disponibles; reinicia tras recogerlas todas y cuando el tiempo lo permita",
        },
        ["Auto Claim Premium Battle Pass"] = {
            "Coletar passe de batalha Premium",
            "Recoger pase de batalla Premium",
        },
        ["Claim unlocked Premium rewards when you own the pass"] = {
            "Coleta recompensas Premium desbloqueadas se possuir o passe",
            "Recoge recompensas Premium desbloqueadas si tienes el pase",
        },
        ["Auto Claim Free Battle Pass"] = {
            "Coletar passe de batalha gratuito",
            "Recoger pase de batalla gratuito",
        },
        ["Claim unlocked Free rewards automatically"] = {
            "Coleta recompensas gratuitas desbloqueadas",
            "Recoge recompensas gratuitas desbloqueadas",
        },
        ["Commandment Totem"] = { "Totem dos mandamentos", "Tótem de los mandamientos" },
        ["Redeem all "] = { "Resgatar todos os ", "Canjear todos los" },
        ["Language"] = { "Idioma", "Idioma" },
        ["English"] = { "English", "English" },
        ["Português (Brasil)"] = { "Português (Brasil)", "Português (Brasil)" },
        ["Português (Portugal)"] = { "Português (Portugal)", "Português (Portugal)" },
        ["Español"] = { "Español", "Español" },
        ["Interface Language"] = { "Idioma da interface", "Idioma de la interfaz" },
        ["Choose the interface language. Changes apply immediately and are saved automatically."] = {
            "Escolha o idioma da interface. As alterações são imediatas e salvas automaticamente.",
            "Elige el idioma de la interfaz. Los cambios se aplican al instante y se guardan automáticamente.",
        },
        ["Titan Passives"] = { "Passivas de titãs", "Pasivas de titanes" },
        ["Titan Passive Target"] = { "Titã para trocar a passiva", "Titán para cambiar la pasiva" },
        ["Halloween"] = { "Halloween", "Halloween" },
        ["Halloween Shop"] = { "Loja de Halloween", "Tienda de Halloween" },
        ["Halloween Craft"] = { "Criação de Halloween", "Fabricación de Halloween" },
        ["Auto Buy Halloween Items"] = { "Comprar itens de Halloween automaticamente", "Comprar objetos de Halloween automáticamente" },
        ["Auto Craft Auras"] = { "Criar auras automaticamente", "Fabricar auras automáticamente" },
        ["Auto Craft Mounts"] = { "Criar montarias automaticamente", "Fabricar monturas automáticamente" },
        ["Farming"] = { "Farm", "Farmeo" },
        ["Farm Raid"] = { "Farm de Raid", "Farmeo de Raid" },
        ["Farm Portal"] = { "Farm de Portal", "Farmeo de Portal" },
        ["Farm Trial"] = { "Farm de Trial", "Farmeo de Trial" },
        ["Marine Invasion"] = { "Invasão da Marinha", "Invasión Marina" },
        ["Weather"] = { "Clima", "Clima" },
        ["Expedition"] = { "Expedição", "Expedición" },
        ["Automation"] = { "Automação", "Automatización" },
        ["Config"] = { "Configurações", "Configuración" },
        ["World Farm"] = { "Farm de mundos", "Farmeo de mundos" },
        ["Secret Bosses"] = { "Chefes secretos", "Jefes secretos" },
        ["Collectibles"] = { "Coletáveis", "Coleccionables" },
        ["Raid Players"] = { "Jogadores da Raid", "Jugadores de Raid" },
        ["Portal Players"] = { "Jogadores do Portal", "Jugadores del Portal" },
        ["Trial Shop"] = { "Loja da Trial", "Tienda de Trial" },
        ["Invasion Automation"] = { "Automação da Invasão", "Automatización de Invasión" },
        ["Invasion Shop"] = { "Loja da Invasão", "Tienda de Invasión" },
        ["Mode Equip Best"] = { "Melhor equipamento por modo", "Mejor equipo por modo" },
        ["Mode Boosts"] = { "Boosts por modo", "Potenciadores por modo" },
        ["General"] = { "Geral", "General" },
        ["Inventory"] = { "Inventário", "Inventario" },
        ["Visual"] = { "Visual", "Visual" },
        ["Weather Equip Best"] = { "Melhor equipamento por clima", "Mejor equipo por clima" },
        ["Weather Boosts"] = { "Boosts por clima", "Potenciadores por clima" },
        ["Weather Webhook"] = { "Webhook de clima", "Webhook del clima" },
        ["Fighters"] = { "Lutadores", "Luchadores" },
        ["Upgrades"] = { "Melhorias", "Mejoras" },
        ["Craft"] = { "Criação", "Fabricación" },
        ["Crafts"] = { "Criações", "Fabricación" },
        ["Configurations"] = { "Configurações", "Configuraciones" },
        ["Reconnect"] = { "Reconexão", "Reconexión" },
        ["Auto Execute"] = { "Execução automática", "Ejecución automática" },
        ["Harbor Auto"] = { "Porto automático", "Puerto automático" },
        ["Harbor Priorities"] = { "Prioridades do porto", "Prioridades del puerto" },
        ["Auto Open Boxes"] = { "Abrir caixas automaticamente", "Abrir cajas automáticamente" },
        ["Webhook Notifications"] = { "Notificações do webhook", "Notificaciones del webhook" },
        ["Discord Mentions"] = { "Menções no Discord", "Menciones de Discord" },
        ["World"] = { "Mundo", "Mundo" },
        ["NPCs"] = { "NPCs", "NPC" },
        ["Select NPCs"] = { "Selecionar NPCs", "Seleccionar NPC" },
        ["Priority Enemy"] = { "Inimigo prioritário", "Enemigo prioritario" },
        ["Select Farm Mode"] = { "Selecionar modo de farm", "Seleccionar modo de farmeo" },
        ["Traditional"] = { "Tradicional", "Tradicional" },
        ["Tradicional"] = { "Tradicional", "Tradicional" },
        ["End Game"] = { "Fim de jogo", "Fin de juego" },
        ["Auto Farm Mob"] = { "Farm automático de inimigos", "Farmeo automático de enemigos" },
        ["Auto Farm Secret Bosses"] = {
            "Farm automático de chefes secretos",
            "Farmeo automático de jefes secretos",
        },
        ["Select Secret Bosses"] = { "Selecionar chefes secretos", "Seleccionar jefes secretos" },
        ["All Secret Bosses"] = { "Todos os chefes secretos", "Todos los jefes secretos" },
        ["Auto Collect Commandment Fragments"] = {
            "Coletar fragmentos de mandamento",
            "Recoger fragmentos de mandamiento",
        },
        ["Server Hop for Commandment Fragments"] = {
            "Trocar de servidor por fragmentos",
            "Cambiar de servidor por fragmentos",
        },
        ["Select Raid"] = { "Selecionar Raid", "Seleccionar Raid" },
        ["Auto Enter Raid"] = { "Entrar automaticamente na Raid", "Entrar automáticamente en Raid" },
        ["Auto Farm Raid"] = { "Farm automático de Raid", "Farmeo automático de Raid" },
        ["Full Auto Raid"] = { "Raid totalmente automática", "Raid totalmente automática" },
        ["Auto Leave"] = { "Sair automaticamente", "Salir automáticamente" },
        ["Leave at Wave"] = { "Sair na onda", "Salir en la oleada" },
        ["Auto Leave at Wave"] = { "Sair automaticamente na onda", "Salir automáticamente en la oleada" },
        ["Select Portal Ranks"] = { "Selecionar ranks de Portal", "Seleccionar rangos de Portal" },
        ["Auto Open Portal"] = { "Abrir Portal automaticamente", "Abrir Portal automáticamente" },
        ["Auto Farm Portal"] = { "Farm automático de Portal", "Farmeo automático de Portal" },
        ["Portal Leave at Wave"] = { "Sair do Portal na onda", "Salir del Portal en la oleada" },
        ["Auto Leave Portal at Wave"] = {
            "Sair do Portal automaticamente na onda",
            "Salir del Portal automáticamente en la oleada",
        },
        ["Auto Enter Trial"] = { "Entrar automaticamente na Trial", "Entrar automáticamente en Trial" },
        ["Auto Farm Trial"] = { "Farm automático de Trial", "Farmeo automático de Trial" },
        ["Auto Enter Invasion"] = {
            "Entrar automaticamente na Invasão",
            "Entrar automáticamente en Invasión",
        },
        ["Auto Farm Invasion"] = { "Farm automático de Invasão", "Farmeo automático de Invasión" },
        ["Auto Leave Invasion"] = {
            "Sair automaticamente da Invasão",
            "Salir automáticamente de Invasión",
        },
        ["Wait for Players"] = { "Esperar jogadores", "Esperar jugadores" },
        ["Wait for Players - "] = { "Esperar jogadores - ", "Esperar jugadores - " },
        ["Minimum Players"] = { "Mínimo de jogadores", "Mínimo de jugadores" },
        ["Auto Join Public "] = {
            "Entrar automaticamente em sala pública de ",
            "Unirse automáticamente a sala pública de ",
        },
        ["Prioritize Marine Invasion"] = { "Priorizar Invasão da Marinha", "Priorizar Invasión Marina" },
        ["Auto Equip Best"] = { "Equipar o melhor automaticamente", "Equipar lo mejor automáticamente" },
        ["Raid Equip Best"] = { "Melhor equipamento para Raid", "Mejor equipo para Raid" },
        ["Portal Equip Best"] = { "Melhor equipamento para Portal", "Mejor equipo para Portal" },
        ["Trial Equip Best"] = { "Melhor equipamento para Trial", "Mejor equipo para Trial" },
        ["Invasion Equip Best"] = { "Melhor equipamento para Invasão", "Mejor equipo para Invasión" },
        ["After Gamemode Equip Best"] = {
            "Melhor equipamento após o modo",
            "Mejor equipo después del modo",
        },
        ["Auto Use Boost"] = { "Usar boost automaticamente", "Usar potenciador automáticamente" },
        ["Auto Use Boosts"] = { "Usar boosts automaticamente", "Usar potenciadores automáticamente" },
        ["Raid Boosts"] = { "Boosts da Raid", "Potenciadores de Raid" },
        ["Portal Boosts"] = { "Boosts do Portal", "Potenciadores del Portal" },
        ["Trial Boosts"] = { "Boosts da Trial", "Potenciadores de Trial" },
        ["Invasion Boosts"] = { "Boosts da Invasão", "Potenciadores de Invasión" },
        ["Auto Buy"] = { "Comprar automaticamente", "Comprar automáticamente" },
        ["Select Items"] = { "Selecionar itens", "Seleccionar objetos" },
        ["Select items"] = { "Selecionar itens", "Seleccionar objetos" },
        ["Juices to Buy"] = { "Sucos para comprar", "Zumos para comprar" },
        ["Auto Buy Juices"] = { "Comprar sucos automaticamente", "Comprar zumos automáticamente" },
        ["Auto Upgrade"] = { "Melhorar automaticamente", "Mejorar automáticamente" },
        ["Auto Merge Weapon"] = { "Fundir armas automaticamente", "Fusionar armas automáticamente" },
        ["Auto Merge Shadows"] = { "Fundir sombras automaticamente", "Fusionar sombras automáticamente" },
        ["Hide Gamemode Rewards"] = { "Ocultar recompensas de modos", "Ocultar recompensas de modos" },
        ["Hide Player Name"] = { "Ocultar nome do jogador", "Ocultar nombre del jugador" },
        ["Hide Teleport Screen"] = { "Ocultar tela de teleporte", "Ocultar pantalla de teletransporte" },
        ["Redeem All Codes"] = { "Resgatar todos os códigos", "Canjear todos los códigos" },
        ["Redeem Codes"] = { "Resgatar códigos", "Canjear códigos" },
        ["Utilities"] = { "Utilidades", "Utilidades" },
        ["Auto Equip Best by Weather"] = { "Equipar o melhor por clima", "Equipar lo mejor según el clima" },
        ["Weather-controlled boosts"] = {
            "Boosts controlados pelo clima",
            "Potenciadores controlados por el clima",
        },
        ["Boost Weather Selection"] = { "Climas para usar boosts", "Climas para usar potenciadores" },
        ["Weather Boost Selection"] = { "Selecionar boosts por clima", "Seleccionar potenciadores por clima" },
        ["Auto Use Weather Boosts"] = {
            "Usar boosts por clima automaticamente",
            "Usar potenciadores por clima automáticamente",
        },
        ["Outside Weather"] = { "Fora dos eventos de clima", "Fuera de los eventos del clima" },
        ["Do Nothing"] = { "Não fazer nada", "No hacer nada" },
        ["All Weather Events"] = { "Todos os eventos de clima", "Todos los eventos del clima" },
        ["Send Weather Alerts"] = { "Enviar alertas de clima", "Enviar alertas del clima" },
        ["Weather Ping Selection"] = { "Climas que devem marcar você", "Climas que deben mencionarte" },
        ["Discord Webhook URL"] = { "URL do webhook do Discord", "URL del webhook de Discord" },
        ["Discord User ID"] = { "ID do usuário do Discord", "ID del usuario de Discord" },
        ["Webhook Status"] = { "Status do webhook", "Estado del webhook" },
        ["Notifications to Send"] = { "Notificações para enviar", "Notificaciones para enviar" },
        ["Notifications That Mention You"] = {
            "Notificações que marcam você",
            "Notificaciones que te mencionan",
        },
        ["Broken Hero Obtained"] = { "Herói Broken obtido", "Héroe Broken obtenido" },
        ["Disconnected"] = { "Desconectado", "Desconectado" },
        ["Inventory Update (every 30s)"] = {
            "Atualização do inventário (a cada 30s)",
            "Actualización del inventario (cada 30 s)",
        },
        ["Your Discord notifications"] = { "Suas notificações no Discord", "Tus notificaciones de Discord" },
        ["Your Discord user ID (optional)"] = {
            "Seu ID do Discord (opcional)",
            "Tu ID de Discord (opcional)",
        },
        ["Discord user ID (blank = no ping)"] = {
            "ID do Discord (vazio = sem menção)",
            "ID de Discord (vacío = sin mención)",
        },
        ["Select Gacha"] = { "Selecionar gacha", "Seleccionar gacha" },
        ["Select Fighters"] = { "Selecionar lutadores", "Seleccionar luchadores" },
        ["Select Upgrade"] = { "Selecionar melhoria", "Seleccionar mejora" },
        ["Select Craft"] = { "Selecionar criação", "Seleccionar fabricación" },
        ["Upgrade Priorities"] = { "Prioridades de melhoria", "Prioridades de mejora" },
        ["Hero Passive Target"] = { "Herói para trocar a passiva", "Héroe para cambiar la pasiva" },
        ["Shadow Passive Target"] = { "Sombra para trocar a passiva", "Sombra para cambiar la pasiva" },
        ["Amulet Building Target"] = { "Amuleto para melhorar", "Amuleto para mejorar" },
        ["Auto Spin Fighters"] = {
            "Invocar lutadores automaticamente",
            "Invocar luchadores automáticamente",
        },
        ["Auto Spin Gacha"] = { "Girar gacha automaticamente", "Girar gacha automáticamente" },
        ["Auto Roll Shadow Passives"] = { "Girar passivas de sombras", "Girar pasivas de sombras" },
        ["Refresh Shadow List"] = { "Atualizar lista de sombras", "Actualizar lista de sombras" },
        ["Auto Craft"] = { "Criar automaticamente", "Fabricar automáticamente" },
        ["Config Name"] = { "Nome da configuração", "Nombre de la configuración" },
        ["Config List"] = { "Lista de configurações", "Lista de configuraciones" },
        ["Save Config"] = { "Salvar configuração", "Guardar configuración" },
        ["Load Config"] = { "Carregar configuração", "Cargar configuración" },
        ["Refresh Config List"] = {
            "Atualizar lista de configurações",
            "Actualizar lista de configuraciones",
        },
        ["Delete Selected Config"] = {
            "Excluir configuração selecionada",
            "Eliminar configuración seleccionada",
        },
        ["Set Auto Load Config"] = { "Definir carregamento automático", "Configurar carga automática" },
        ["Auto Reconnect"] = { "Reconectar automaticamente", "Reconectar automáticamente" },
        ["Loader URL (optional)"] = { "URL do carregador (opcional)", "URL del cargador (opcional)" },
        ["Auto Execute on Server Change"] = {
            "Executar ao trocar de servidor",
            "Ejecutar al cambiar de servidor",
        },
        ["Execute after teleport"] = { "Executar após teleporte", "Ejecutar después del teletransporte" },
        ["Native Harbor automation"] = { "Automação nativa do porto", "Automatización nativa del puerto" },
        ["Auto Send - "] = { "Enviar automaticamente - ", "Enviar automáticamente - " },
        ["Auto Collect - "] = { "Coletar automaticamente - ", "Recoger automáticamente - " },
        ["Fill Empty Slots"] = { "Preencher espaços vazios", "Rellenar espacios vacíos" },
        ["Replace with Better Crewmates"] = {
            "Substituir por tripulantes melhores",
            "Sustituir por mejores tripulantes",
        },
        ["Prioritize"] = { "Priorizar", "Priorizar" },
        ["Crewmate Priority"] = { "Prioridade de tripulantes", "Prioridad de tripulantes" },
        ["Ship Priority"] = { "Prioridade de barcos", "Prioridad de barcos" },
        ["Part Priority"] = { "Prioridade de peças", "Prioridad de piezas" },
        ["Move Up - "] = { "Mover para cima - ", "Subir - " },
        ["Move Down - "] = { "Mover para baixo - ", "Bajar - " },
        ["Enable / Disable - "] = { "Ativar / desativar - ", "Activar / desactivar - " },
        ["Refresh - "] = { "Atualizar - ", "Actualizar - " },
        ["Currency rewards"] = { "Recompensas de moedas", "Recompensas de monedas" },
        ["Currency Box Rewards"] = { "Recompensas de caixas de moedas", "Recompensas de cajas de monedas" },
        ["Auto Open Currency Boxes"] = {
            "Abrir caixas de moedas automaticamente",
            "Abrir cajas de monedas automáticamente",
        },
        ["Auto Open Fruit Boxes"] = {
            "Abrir caixas de frutas automaticamente",
            "Abrir cajas de frutas automáticamente",
        },
        ["None"] = { "Nenhum", "Ninguno" },
        ["Select..."] = { "Selecionar...", "Seleccionar..." },
        ["Select boosts"] = { "Selecionar boosts", "Seleccionar potenciadores" },
        ["Select boost items"] = { "Selecionar itens de boost", "Seleccionar potenciadores" },
        ["Select weather events"] = { "Selecionar eventos de clima", "Seleccionar eventos del clima" },
        ["Choose a raid"] = { "Escolha uma Raid", "Elige una Raid" },
        ["Choose one or more enemies"] = { "Escolha um ou mais inimigos", "Elige uno o más enemigos" },
        ["Choose the NPC world"] = { "Escolha o mundo dos NPCs", "Elige el mundo de los NPC" },
        ["Choose one or more Trial Shop items to buy"] = {
            "Escolha os itens da loja da Trial para comprar",
            "Elige los objetos de la tienda de Trial que deseas comprar",
        },
        ["Empty selection farms all Secret bosses."] = {
            "A seleção vazia inclui todos os chefes secretos.",
            "Una selección vacía incluye todos los jefes secretos.",
        },
        ["Cycle through every available Secret boss in unlocked worlds"] = {
            "Alterna entre os chefes secretos dos mundos desbloqueados",
            "Alterna entre los jefes secretos de mundos desbloqueados",
        },
        ["Prefer this NPC when choosing the next target. Select NPCs above first."] = {
            "Prioriza este NPC como próximo alvo. Selecione os NPCs acima primeiro.",
            "Prioriza este NPC como siguiente objetivo. Selecciona primero los NPC de arriba.",
        },
        ["Teleport, attack and repeat until disabled"] = {
            "Teleporta, ataca e repete até desativar",
            "Teletransporta, ataca y repite hasta desactivarlo",
        },
        ["Teleport to and attack enemies in your raid"] = {
            "Teleporta até os inimigos da sua Raid e ataca",
            "Teletransporta hasta los enemigos de tu Raid y ataca",
        },
        ["Teleport to and attack enemies in your trial"] = {
            "Teleporta até os inimigos da sua Trial e ataca",
            "Teletransporta hasta los enemigos de tu Trial y ataca",
        },
        ["Teleports to and attacks enemies inside the selected portal."] = {
            "Teleporta até os inimigos do Portal selecionado e ataca.",
            "Teletransporta hasta los enemigos del Portal seleccionado y ataca.",
        },
        ["Pauses farming, leaves any gamemode and confirms fragment pickup before resuming."] = {
            "Pausa o farm, sai do modo e confirma a coleta do fragmento antes de continuar.",
            "Pausa el farmeo, sale del modo y confirma la recogida del fragmento antes de continuar.",
        },
        ["When auto collect is on, changes servers after pickup or when none is found."] = {
            "Com a coleta automática ligada, troca de servidor após coletar ou quando não encontra fragmentos.",
            "Con la recogida automática activa, cambia de servidor tras recoger o si no encuentra fragmentos.",
        },
        ["Use a ticket or farm enemies that drop it"] = {
            "Usa um ticket ou farma os inimigos que o deixam",
            "Usa un ticket o farmea enemigos que lo sueltan",
        },
        ["Runs every raid with tickets. When all tickets end, farms every ticket to 250, then repeats."] = {
            "Faz as Raids com tickets disponíveis. Quando acabam, farma até 250 de cada ticket e repete.",
            "Completa las Raids con tickets disponibles. Cuando se agotan, farmea hasta 250 de cada ticket y repite.",
        },
        ["Join The Hallway when entry opens"] = {
            "Entra no Hallway quando a entrada abre",
            "Entra en Hallway cuando se abre la entrada",
        },
        ["Leave the selected raid at the configured wave"] = {
            "Sai da Raid selecionada na onda definida",
            "Sale de la Raid seleccionada en la oleada indicada",
        },
        ["Leave your trial at the configured wave"] = {
            "Sai da Trial na onda definida",
            "Sale de la Trial en la oleada indicada",
        },
        ["Leave when this wave is reached (1-100)"] = {
            "Sai ao atingir esta onda (1–100)",
            "Sale al alcanzar esta oleada (1–100)",
        },
        ["Leave when this wave is reached (1-50)"] = {
            "Sai ao atingir esta onda (1–50)",
            "Sale al alcanzar esta oleada (1–50)",
        },
        ["Leave the Portal at this wave (1-100)."] = {
            "Sai do Portal nesta onda (1–100).",
            "Sale del Portal en esta oleada (1–100).",
        },
        ["Leave the selected Portal Rank at the configured wave."] = {
            "Sai do rank de Portal selecionado na onda definida.",
            "Sale del rango de Portal seleccionado en la oleada indicada.",
        },
        ["Opens the selected Portal Rank whenever its ticket is available."] = {
            "Abre o rank de Portal selecionado quando há tickets.",
            "Abre el rango de Portal seleccionado cuando hay tickets.",
        },
        ["Uses every ticket from the weakest selected rank before moving to the next (C, B, A, S)."] = {
            "Usa os tickets do menor rank selecionado antes do próximo (C, B, A, S).",
            "Usa los tickets del menor rango seleccionado antes del siguiente (C, B, A, S).",
        },
        ["Auto Enter/Open creates your room; wait before Start. Includes yourself."] = {
            "Entrar/abrir automaticamente cria sua sala; espera antes de iniciar. Inclui você.",
            "Entrar/abrir automáticamente crea tu sala; espera antes de iniciar. Te incluye a ti.",
        },
        ["Total players required before starting, including you."] = {
            "Total de jogadores necessários para iniciar, incluindo você.",
            "Total de jugadores necesarios para empezar, incluyéndote.",
        },
        ["Join any public room while it is Opened, before the host starts it."] = {
            "Entra em uma sala pública aberta antes de o anfitrião iniciar.",
            "Entra en una sala pública abierta antes de que empiece el anfitrión.",
        },
        ["Equips the best full setup once when entering a Raid, Trial or Portal."] = {
            "Equipa o melhor conjunto ao entrar em Raid, Trial ou Portal.",
            "Equipa el mejor conjunto al entrar en Raid, Trial o Portal.",
        },
        ["Attribute prioritized once after leaving a Raid, Trial or Portal."] = {
            "Atributo priorizado após sair de Raid, Trial ou Portal.",
            "Atributo priorizado al salir de Raid, Trial o Portal.",
        },
        ["Attribute prioritized when a Raid starts."] = {
            "Atributo priorizado ao iniciar uma Raid.",
            "Atributo priorizado al iniciar una Raid.",
        },
        ["Attribute prioritized when entering a Portal."] = {
            "Atributo priorizado ao entrar em um Portal.",
            "Atributo priorizado al entrar en un Portal.",
        },
        ["Attribute prioritized when The Hallway starts."] = {
            "Atributo priorizado ao iniciar o Hallway.",
            "Atributo priorizado al iniciar Hallway.",
        },
        ["All boost items, including those not owned."] = {
            "Todos os boosts, incluindo os que você não possui.",
            "Todos los potenciadores, incluidos los que no tienes.",
        },
        ["Uses selected boosts in Raid, Trial and Portal. Pauses outside and resumes on return."] = {
            "Usa os boosts selecionados nos modos. Pausa fora e retoma ao voltar.",
            "Usa los potenciadores seleccionados en los modos. Pausa fuera y reanuda al volver.",
        },
        ["Pause after the Trial; resume when entering the next Trial."] = {
            "Pausa após a Trial e retoma na próxima.",
            "Pausa después de la Trial y reanuda en la siguiente.",
        },
        ["Use or resume these boosts in Portal; pause outside."] = {
            "Usa ou retoma estes boosts no Portal; pausa fora.",
            "Usa o reanuda estos potenciadores en el Portal; pausa fuera.",
        },
        ["Shared enable switch for mode automation. This mode uses its own selections below."] = {
            "Ativação compartilhada entre os modos. Este modo usa suas seleções abaixo.",
            "Activación compartida entre modos. Este modo usa sus selecciones de abajo.",
        },
        ["Buy one at a time while you have shards and stock is available. No paid restocks."] = {
            "Compra um por vez enquanto houver fragmentos e estoque. Sem reposições pagas.",
            "Compra uno a la vez mientras haya fragmentos y existencias. Sin reposiciones de pago.",
        },
        ["Uses Pirate Shards, one purchase at a time. Respects stock and balance; no paid restocks."] = {
            "Usa Pirate Shards, uma compra por vez. Respeita saldo e estoque; sem reposições pagas.",
            "Usa Pirate Shards, una compra a la vez. Respeta saldo y existencias; sin reposiciones de pago.",
        },
        ["When Auto Enter is enabled, leave Raid or Portal for an open Invasion. Trial retains highest priority."] = {
            "Com a entrada automática ligada, sai de Raid ou Portal para a Invasão aberta. A Trial mantém prioridade máxima.",
            "Con entrada automática, sale de Raid o Portal hacia una Invasión abierta. La Trial mantiene la prioridad máxima.",
        },
        ["Trial keeps priority. Entry follows the game's schedule. Wait for Players pauses Zeen farming only; the server controls the event start."] = {
            "A Trial mantém prioridade. A entrada segue o horário do jogo. Esperar jogadores pausa apenas o farm do TBL; o servidor inicia o evento.",
            "La Trial mantiene prioridad. La entrada sigue el horario del juego. Esperar jugadores solo pausa el farmeo de TBL; el servidor inicia el evento.",
        },
        ["Mode automation"] = { "Automação de modos", "Automatización de modos" },
        ["Scheduled event"] = { "Evento agendado", "Evento programado" },
        ["Use the shared Auto Equip Best and Auto Use Boosts switches on this page. Weather boost rules retain priority."] = {
            "Use os controles compartilhados de equipamento e boosts nesta página. As regras de clima mantêm prioridade.",
            "Usa los controles compartidos de equipo y potenciadores de esta página. Las reglas del clima mantienen prioridad.",
        },
        ["Send periodic keyboard activity to prevent idle disconnection."] = {
            "Envia atividade periódica de teclado para evitar desconexão por inatividade.",
            "Envía actividad periódica del teclado para evitar desconexión por inactividad.",
        },
        ["Merge duplicate weapons into stars. Equipped and locked weapons are never consumed."] = {
            "Funde armas repetidas em estrelas. Armas equipadas ou bloqueadas não são consumidas.",
            "Fusiona armas repetidas en estrellas. No consume armas equipadas ni bloqueadas.",
        },
        ["Merge duplicate Shadows using the game plan; protects locked, equipped and spinning sacrifices."] = {
            "Funde sombras repetidas usando as regras do jogo; protege as bloqueadas, equipadas ou em rolagem.",
            "Fusiona sombras repetidas según las reglas del juego; protege las bloqueadas, equipadas o en giro.",
        },
        ["Hide your overhead nickname."] = {
            "Oculta o apelido acima do personagem.",
            "Oculta el nombre sobre el personaje.",
        },
        ["Hide Raid, Trial and world teleport overlays. Teleport timing is unchanged."] = {
            "Oculta as telas de teleporte. O tempo do teleporte não muda.",
            "Oculta las pantallas de teletransporte. El tiempo no cambia.",
        },
        ["Hide the Raid and Trial results screen. Rewards are still received."] = {
            "Oculta os resultados de Raid e Trial. As recompensas continuam sendo recebidas.",
            "Oculta los resultados de Raid y Trial. Las recompensas se siguen recibiendo.",
        },
        ["Detects the active weather and equips the best full setup for its configured attribute."] = {
            "Detecta o clima ativo e equipa o melhor conjunto para o atributo escolhido.",
            "Detecta el clima activo y equipa el mejor conjunto para el atributo elegido.",
        },
        ["Optional Equip Best applied once when every weather event ends."] = {
            "Equipamento opcional aplicado quando todos os eventos de clima terminam.",
            "Equipo opcional que se aplica cuando terminan todos los eventos del clima.",
        },
        ["Consumes selected items only during selected weather. Resumes paused duration before using a new item."] = {
            "Usa os itens apenas nos climas selecionados. Retoma a duração pausada antes de usar outro item.",
            "Usa los objetos solo en los climas seleccionados. Reanuda la duración pausada antes de usar otro objeto.",
        },
        ["Uses one selected boost when needed, pauses it outside selected weather, and resumes its remaining duration when that weather returns. Weather control takes priority over Modes for the same boost. Disabling pauses boosts managed here."] = {
            "Usa um boost quando necessário, pausa fora dos climas escolhidos e retoma a duração restante quando voltam. O clima tem prioridade sobre os modos. Desativar pausa os boosts gerenciados aqui.",
            "Usa un potenciador cuando hace falta, pausa fuera de los climas elegidos y reanuda la duración restante cuando vuelven. El clima tiene prioridad sobre los modos. Desactivar pausa los potenciadores gestionados aquí.",
        },
        ["All other weather alerts are still sent, without a mention."] = {
            "Os demais alertas de clima continuam sendo enviados, sem menção.",
            "Los demás avisos del clima se siguen enviando, sin mención.",
        },
        ["Paste your full Discord webhook URL below. Sends all new weather events to your webhook; weather selection only controls mentions. A blank URL disables delivery."] = {
            "Cole a URL completa do webhook abaixo. Envia todos os novos climas; a seleção controla apenas as menções. URL vazia desativa o envio.",
            "Pega la URL completa del webhook abajo. Envía todos los nuevos climas; la selección solo controla menciones. Una URL vacía desactiva el envío.",
        },
        ["Only mentions you for enabled notifications selected here."] = {
            "Marca você apenas nas notificações ativas selecionadas aqui.",
            "Solo te menciona en las notificaciones activas seleccionadas aquí.",
        },
        ["Sends only the selected alerts to your URL. Includes Roblox username, new heroes and inventory gains; no IP or device data. Inventory reports are sent every 30 seconds, including when nothing changed. Disconnect delivery is best effort and cannot work after a crash or loss of internet."] = {
            "Envia apenas os alertas selecionados para sua URL. Inclui nome do Roblox, novos heróis e ganhos no inventário, sem IP ou dados do dispositivo. Envia resumos a cada 30 segundos, mesmo sem mudanças. O aviso de desconexão depende de o cliente e a internet continuarem funcionando.",
            "Envía solo los avisos seleccionados a tu URL. Incluye nombre de Roblox, nuevos héroes y ganancias del inventario, sin IP ni datos del dispositivo. Envía resúmenes cada 30 segundos, incluso sin cambios. El aviso de desconexión depende de que el cliente e internet sigan funcionando.",
        },
        ["Uses available tokens and native spin slots"] = {
            "Usa as moedas disponíveis e os espaços de giro do jogo",
            "Usa las monedas disponibles y los espacios de giro del juego",
        },
        ["Uses Gold and shares spin slots with gachas"] = {
            "Usa ouro e compartilha os espaços de giro com gachas",
            "Usa oro y comparte espacios de giro con gachas",
        },
        ["Selection follows your native simultaneous spin limit."] = {
            "Selecione até dois por lista. Todos os giros compartilham o limite do jogo.",
            "Selecciona hasta dos por lista. Todos los giros comparten el límite del juego.",
        },
        ["Character to reroll when Hero Passives is selected in Select Gacha. Uses the stop targets configured in the game's Manage menu."] = {
            "Herói para trocar a passiva quando essa opção estiver no gacha. Usa as condições de parada do menu de gerenciamento do jogo.",
            "Héroe al que cambiar la pasiva cuando esa opción esté en el gacha. Usa las condiciones de parada del menú de gestión del juego.",
        },
        ["Required only for Amulet Building; rerolls the selected amulet"] = {
            "Necessário apenas para melhorar amuletos; altera o amuleto selecionado",
            "Necesario solo para mejorar amuletos; cambia el amuleto seleccionado",
        },
        ["Select the Shadow to roll. Stop targets come from the game's Manage menu."] = {
            "Selecione a sombra. As condições de parada vêm do menu de gerenciamento do jogo.",
            "Selecciona la sombra. Las condiciones de parada vienen del menú de gestión del juego.",
        },
        ["Uses Shadow Passive Coins and available Spin Manager slots."] = {
            "Usa moedas de passiva de sombra e espaços de giro disponíveis.",
            "Usa monedas de pasivas de sombra y espacios de giro disponibles.",
        },
        ["One purchase per selected priority, in rotation; waits for its cost"] = {
            "Uma compra por prioridade selecionada, em rotação; espera ter saldo",
            "Una compra por prioridad seleccionada, por turnos; espera tener saldo",
        },
        ["Advances the selected totem using its materials. Commandment Totem uses Commandment Fragments. Stops at the final stage."] = {
            "Melhora o totem selecionado usando seus materiais. O totem de mandamentos usa fragmentos de mandamento. Para no estágio final.",
            "Mejora el tótem seleccionado usando sus materiales. El tótem de mandamientos usa fragmentos de mandamiento. Se detiene en la etapa final.",
        },
        ["Name used when saving."] = { "Nome usado ao salvar.", "Nombre usado al guardar." },
        ["Save all current automation selections and toggles."] = {
            "Salva todas as seleções e ativações de automação.",
            "Guarda todas las selecciones y activaciones de automatización.",
        },
        ["Load the selected configuration."] = {
            "Carrega a configuração selecionada.",
            "Carga la configuración seleccionada.",
        },
        ["Delete the selected configuration."] = {
            "Exclui a configuração selecionada.",
            "Elimina la configuración seleccionada.",
        },
        ["Select a configuration to load or delete."] = {
            "Selecione uma configuração para carregar ou excluir.",
            "Selecciona una configuración para cargar o eliminar.",
        },
        ["Refresh saved configuration names."] = {
            "Atualiza os nomes das configurações salvas.",
            "Actualiza los nombres de las configuraciones guardadas.",
        },
        ["Automatically load the selected config next time the script runs."] = {
            "Carrega a configuração selecionada na próxima execução.",
            "Carga la configuración seleccionada en la próxima ejecución.",
        },
        ["Reconnects to this experience after a Roblox disconnect."] = {
            "Reconecta a esta experiência após uma desconexão.",
            "Reconecta a esta experiencia después de una desconexión.",
        },
        ["Requires queue_on_teleport. The packed release carries its own source; an optional loader URL can override it. Your executor must support the destination session."] = {
            "Requer queue_on_teleport. A versão ofuscada inclui o próprio código; a URL opcional pode substituí-lo. O executor precisa suportar a sessão de destino.",
            "Requiere queue_on_teleport. La versión ofuscada incluye su código; la URL opcional puede sustituirlo. El ejecutor debe admitir la sesión de destino.",
        },
        ["These controls update the game's own Auto settings. They are saved by the game and respect unlock requirements. Configure each dock's ship and route in Harbor first. Auto Upgrade spends Berries."] = {
            "Estes controles alteram o Auto do jogo, que salva as opções e respeita os desbloqueios. Configure primeiro o barco e a rota de cada doca no porto. A melhoria automática gasta Berries.",
            "Estos controles cambian el Auto del juego, que guarda las opciones y respeta los desbloqueos. Configura primero el barco y la ruta de cada muelle en el puerto. La mejora automática gasta Berries.",
        },
        ["Select box → reward combinations in one dropdown. Multiple rewards rotate fairly. Only selected combinations are opened, one box at a time with inventory confirmation."] = {
            "Selecione caixa → recompensa em uma lista. As recompensas alternam entre si. Abre apenas as combinações selecionadas, uma caixa por vez, aguardando confirmação.",
            "Selecciona caja → recompensa en una lista. Las recompensas se alternan. Solo abre las combinaciones seleccionadas, una caja a la vez, esperando confirmación.",
        },
        ["Energy"] = { "Energia", "Energía" },
        ["Damage"] = { "Dano", "Daño" },
        ["Gold"] = { "Ouro", "Oro" },
        ["Drop"] = { "Drops", "Botín" },
        ["Card Luck"] = { "Sorte de heróis", "Suerte de héroes" },
        ["Gacha Luck"] = { "Sorte de gacha", "Suerte de gacha" },
        ["Attack Speed"] = { "Velocidade de ataque", "Velocidad de ataque" },
        ["Attack Range"] = { "Alcance de ataque", "Alcance de ataque" },
        ["Walk Speed"] = { "Velocidade de movimento", "Velocidad de movimiento" },
        ["Critical Chance"] = { "Chance de crítico", "Probabilidad de crítico" },
        ["Critical Damage"] = { "Dano crítico", "Daño crítico" },
        ["Energy Potion"] = { "Poção de energia", "Poción de energía" },
        ["Damage Potion"] = { "Poção de dano", "Poción de daño" },
        ["Gold Potion"] = { "Poção de ouro", "Poción de oro" },
        ["Drop Potion"] = { "Poção de drops", "Poción de botín" },
        ["Luck Potion"] = { "Poção de sorte", "Poción de suerte" },
        ["Energy Juice"] = { "Suco de energia", "Zumo de energía" },
        ["Damage Juice"] = { "Suco de dano", "Zumo de daño" },
        ["Gold Juice"] = { "Suco de ouro", "Zumo de oro" },
        ["Drop Juice"] = { "Suco de drops", "Zumo de botín" },
        ["Luck Juice"] = { "Suco de sorte", "Zumo de suerte" },
        ["Currency Box"] = { "Caixa de moedas", "Caja de monedas" },
        ["Devil Fruit Box"] = { "Caixa de frutas", "Caja de frutas" },
        ["Lightning"] = { "Relâmpagos", "Relámpagos" },
        ["Meteor Shower"] = { "Chuva de meteoros", "Lluvia de meteoros" },
        ["Golden Sunset"] = { "Pôr do sol dourado", "Atardecer dorado" },
        ["Blessed Skies"] = { "Céus abençoados", "Cielos bendecidos" },
        ["Rain"] = { "Chuva", "Lluvia" },
        ["Snow"] = { "Neve", "Nieve" },
        ["Toxic"] = { "Tóxico", "Tóxico" },
        ["Aurora"] = { "Aurora", "Aurora" },
        ["Eclipse"] = { "Eclipse", "Eclipse" },
        ["Boost"] = { "Bônus", "Bonificación" },
        ["Rarity"] = { "Raridade", "Rareza" },
        ["Berries"] = { "Berries", "Berries" },
        ["Devil Fruit"] = { "Fruta", "Fruta" },
        ["Speed"] = { "Velocidade", "Velocidad" },
        ["Hull"] = { "Casco", "Casco" },
        ["Comfort"] = { "Conforto", "Comodidad" },
        ["Cargo"] = { "Carga", "Carga" },
        ["Crew Slots"] = { "Espaços de tripulação", "Espacios de tripulación" },
        ["Sails"] = { "Velas", "Velas" },
        ["Cabins"] = { "Cabines", "Camarotes" },
        ["Cargo Hold"] = { "Porão de carga", "Bodega" },
        ["Navigation Room"] = { "Sala de navegação", "Sala de navegación" },
        ["Crew Deck"] = { "Convés da tripulação", "Cubierta de tripulación" },
        ["Small Boat"] = { "Barco pequeno", "Barco pequeño" },
        ["Invalid Discord ID"] = { "ID do Discord inválido", "ID de Discord no válido" },
        ["Invalid webhook"] = { "Webhook inválido", "Webhook no válido" },
        ["Invalid Webhook URL"] = { "URL do webhook inválida", "URL de webhook no válida" },
        ["Invalid wave"] = { "Onda inválida", "Oleada no válida" },
        ["Selection limit"] = { "Limite de seleção", "Límite de selección" },
        ["Auto Execute failed"] = { "Falha na execução automática", "Error de ejecución automática" },
        ["Auto Open stopped"] = { "Abertura automática interrompida", "Apertura automática detenida" },
        ["Auto Buy Juices stopped"] = { "Compra de sucos interrompida", "Compra de zumos detenida" },
        ["Enter a whole number from 1 to 100."] = {
            "Digite um número inteiro de 1 a 100.",
            "Introduce un número entero del 1 al 100.",
        },
        ["Enter a whole number from 1 to 50."] = {
            "Digite um número inteiro de 1 a 50.",
            "Introduce un número entero del 1 al 50.",
        },
        ["Enter your 17-20 digit Discord user ID, not your username."] = {
            "Digite seu ID do Discord com 17–20 dígitos, não seu nome.",
            "Introduce tu ID de Discord de 17–20 dígitos, no tu nombre.",
        },
        ["Use your 17–20 digit Discord user ID, not your username."] = {
            "Use seu ID do Discord com 17–20 dígitos, não seu nome.",
            "Usa tu ID de Discord de 17–20 dígitos, no tu nombre.",
        },
        ["Paste the complete Discord webhook URL, not only its ID."] = {
            "Cole a URL completa do webhook, não apenas o ID.",
            "Pega la URL completa del webhook, no solo su ID.",
        },
        ["Paste the full Discord webhook URL, including its token."] = {
            "Cole a URL completa do webhook, incluindo o token.",
            "Pega la URL completa del webhook, incluido el token.",
        },
        ["Your executor has no queue_on_teleport support."] = {
            "Seu executor não oferece suporte a queue_on_teleport.",
            "Tu ejecutor no admite queue_on_teleport.",
        },
        ["Executor file APIs are unavailable."] = {
            "As funções de arquivos do executor estão indisponíveis.",
            "Las funciones de archivos del ejecutor no están disponibles.",
        },
        ["Inventory did not confirm the last box. Re-enable to retry."] = {
            "O inventário não confirmou a última caixa. Ative novamente para tentar.",
            "El inventario no confirmó la última caja. Actívalo de nuevo para reintentar.",
        },
        ["The last purchase was not confirmed. Check your balance and shop access before retrying."] = {
            "A última compra não foi confirmada. Verifique saldo e acesso à loja antes de tentar novamente.",
            "La última compra no se confirmó. Comprueba el saldo y el acceso a la tienda antes de reintentar.",
        },
        ["Seu Name e DisplayName do Roblox serao enviados ao Discord do responsavel pelo Zeen."] = {
            "Seu nome e nome de exibição do Roblox serão enviados ao Discord do responsável pelo Zeen.",
            "Tu nombre y nombre visible de Roblox se enviarán al Discord del responsable de Zeen.",
        },
        ["Zeen - Registro de uso"] = { "Zeen - Registro de uso", "Zeen - Registro de uso" },
        ["Enabled"] = { "Ativado", "Activado" },
        ["Disabled"] = { "Desativado", "Desactivado" },
        ["Enable"] = { "Ativar", "Activar" },
        ["Disable"] = { "Desativar", "Desactivar" },
        ["Saved: "] = { "Salvo: ", "Guardado: " },
        ["Loaded: "] = { "Carregado: ", "Cargado: " },
        ["Disabled: "] = { "Desativados: ", "Desactivados: " },
        ["Ticket: "] = { "Ticket: ", "Ticket: " },
        ["Owned: "] = { "Quantidade: ", "Cantidad: " },
        ["Select"] = { "Selecionar", "Seleccionar" },
        ["Search"] = { "Pesquisar", "Buscar" },
        ["Search..."] = { "Pesquisar...", "Buscar..." },
        ["Search.."] = { "Pesquisar...", "Buscar..." },
        ["No results"] = { "Nenhum resultado", "Sin resultados" },
        ["Auto Claim Daily"] = { "Coletar recompensa diária", "Recoger recompensa diaria" },
        ["Auto Claim Playtime"] = { "Coletar recompensas de tempo", "Recoger recompensas de tiempo" },
        ["Auto Claim Achievements"] = { "Coletar conquistas", "Recoger logros" },
        ["Auto Claim Quests"] = { "Coletar missões", "Recoger misiones" },
        ["Auto Claim Battlepass"] = { "Coletar passe de batalha", "Recoger pase de batalla" },
        ["Common"] = { "Comum", "Común" },
        ["Rare"] = { "Raro", "Raro" },
        ["Epic"] = { "Épico", "Épico" },
        ["Legendary"] = { "Lendário", "Legendario" },
        ["Mythical"] = { "Mítico", "Mítico" },
        ["Secret"] = { "Secreto", "Secreto" },
        ["All"] = { "Todos", "Todos" },
        ["Do Not Open"] = { "Não abrir", "No abrir" },
        ["Currency"] = { "Moedas", "Monedas" },
        ["Juice"] = { "Suco", "Zumo" },
        ["Potion"] = { "Poção", "Poción" },
        ["Boosts"] = { "Boosts", "Potenciadores" },
        ["Energy Boost"] = { "Bônus de energia", "Bonificación de energía" },
        ["Damage Boost"] = { "Bônus de dano", "Bonificación de daño" },
        ["Inventory Update — 30 seconds"] = {
            "Atualização do inventário — 30 segundos",
            "Actualización del inventario — 30 segundos",
        },
        ["Disconnected from Roblox"] = { "Desconectado do Roblox", "Desconectado de Roblox" },
        ["No new inventory items detected in the last 30 seconds."] = {
            "Nenhum novo item detectado no inventário nos últimos 30 segundos.",
            "No se detectaron objetos nuevos en el inventario en los últimos 30 segundos.",
        },
        ["Weapon"] = { "Arma", "Arma" },
        ["Hero"] = { "Herói", "Héroe" },
        ["Warrior"] = { "Guerreiro", "Guerrero" },
        ["Avatar"] = { "Avatar", "Avatar" },
        ["Mount"] = { "Montaria", "Montura" },
        ["Wing"] = { "Asa", "Ala" },
        ["Accessory"] = { "Acessório", "Accesorio" },
        ["Jewel"] = { "Joia", "Joya" },
        ["Crewmate"] = { "Tripulante", "Tripulante" },
        ["Amulet"] = { "Amuleto", "Amuleto" },
        ["Item"] = { "Item", "Objeto" },
        ["Coins"] = { "Moedas", "Monedas" },
        ["Shards"] = { "Fragmentos", "Fragmentos" },
        ["Auto Collect"] = { "Coletar automaticamente", "Recoger automáticamente" },
        ["Auto Send"] = { "Enviar automaticamente", "Enviar automáticamente" },
        ["Raid Minimum Players"] = { "Mínimo de jogadores na Raid", "Mínimo de jugadores en Raid" },
        ["Portal Minimum Players"] = { "Mínimo de jogadores no Portal", "Mínimo de jugadores en Portal" },
        ["Attribute used by Equip Best while "] = {
            "Atributo usado pelo melhor equipamento enquanto ",
            "Atributo usado por el mejor equipo mientras ",
        },
        [" is active."] = { " está ativo.", " está activo." },
    }

    local valid = { en = true, ["pt-BR"] = true, ["pt-PT"] = true, es = true }
    local english = {
        ["Tradicional"] = "Traditional",
        ["Seu Name e DisplayName do Roblox serao enviados ao Discord do responsavel pelo Zeen."] = "Your Roblox username and display name will be sent to the Zeen owner's Discord.",
        ["Zeen - Registro de uso"] = "Zeen - Usage report",
    }
    local portuguese = {
        { "usuário", "utilizador" },
        { "Usuário", "Utilizador" },
        { "tela", "ecrã" },
        { "Tela", "Ecrã" },
        { "salvar", "guardar" },
        { "Salvar", "Guardar" },
        { "salvas", "guardadas" },
        { "salva", "guarda" },
        { "Salva", "Guarda" },
        { "salvo", "guardado" },
        { "Salvo", "Guardado" },
        { "coletar", "recolher" },
        { "Coletar", "Recolher" },
        { "coleta", "recolha" },
        { "Coleta", "Recolha" },
        { "Coletáveis", "Colecionáveis" },
        { "suco", "sumo" },
        { "Suco", "Sumo" },
        { "estoque", "stock" },
        { "Digite", "Introduza" },
        { "digite", "introduza" },
        { "gerenciamento", "gestão" },
        { "gerenciados", "geridos" },
        { "você", "o utilizador" },
        { "compartilhada", "partilhada" },
        { "compartilhados", "partilhados" },
        { "compartilham", "partilham" },
        { "compartilha", "partilha" },
        { "arquivos", "ficheiros" },
    }
    local function european(value)
        for _, pair in ipairs(portuguese) do
            value = value:gsub(pair[1], pair[2])
        end
        return value
    end
    local keys = {}
    for key in pairs(catalog) do
        keys[#keys + 1] = key
    end
    table.sort(keys, function(a, b)
        return #a > #b
    end)
    local autonyms = {
        English = true,
        ["Português (Brasil)"] = true,
        ["Português (Portugal)"] = true,
        ["Español"] = true,
    }
    function Localization:translate(text)
        if type(text) ~= "string" or text == "" then
            return text
        end
        if autonyms[text] or text:find("https://", 1, true) or text:find("http://", 1, true) then
            return text
        end
        if self.locale == "en" then
            return english[text] or text
        end
        if self.cache[text] then
            return self.cache[text]
        end
        local index = self.locale == "es" and 2 or 1
        local direct = catalog[text]
        local translated
        if direct then
            translated = direct[index]
        else
            local result, pos = {}, 1
            while pos <= #text do
                local bestStart, bestEnd, bestKey
                for _, key in ipairs(keys) do
                    local a, b = text:find(key, pos, true)
                    if a then
                        local before = a > 1 and text:sub(a - 1, a - 1) or ""
                        local after = text:sub(b + 1, b + 1)
                        local left = not key:sub(1, 1):match("%w") or not before:match("%w")
                        local right = not key:sub(-1):match("%w") or not after:match("%w")
                        if
                            left
                            and right
                            and (not bestStart or a < bestStart or (a == bestStart and b > bestEnd))
                        then
                            bestStart, bestEnd, bestKey = a, b, key
                        end
                    end
                end
                if not bestStart then
                    result[#result + 1] = text:sub(pos)
                    break
                end
                result[#result + 1] = text:sub(pos, bestStart - 1)
                result[#result + 1] = catalog[bestKey][index]
                pos = bestEnd + 1
            end
            translated = table.concat(result)
            translated = translated:gsub(
                "(%d+) selected: ",
                self.locale == "es" and "%1 seleccionados: " or "%1 selecionados: "
            )
        end
        if self.locale == "pt-PT" then
            translated = european(translated)
        end
        self.cache[text] = translated
        return translated
    end
    function Localization:setLocale(locale)
        if not valid[locale] then
            return false
        end
        self.locale = locale
        self.cache = {}
        local count = 0
        for _, binding in pairs(self.bindings) do
            binding.render()
            count += 1
            if count % 40 == 0 then
                task.wait()
            end
        end
        return true
    end
    function Localization:attach(root, extras)
        self:detach()
        self.generation = (self.generation or 0) + 1
        local generation = self.generation
        local pending = {}
        local scheduled = false
        local function queue(binding)
            pending[binding] = true
            if scheduled then
                return
            end
            scheduled = true
            task.delay(0.12, function()
                scheduled = false
                if self.generation ~= generation then
                    return
                end
                local batch = pending
                pending = {}
                local count = 0
                for item in pairs(batch) do
                    if self.generation ~= generation then
                        return
                    end
                    item.render()
                    count += 1
                    if count % 40 == 0 then
                        task.wait()
                    end
                end
            end)
        end
        local function watch(instance)
            if self.bindings[instance] then
                return
            end
            local property
            if instance:IsA("TextBox") then
                property = "PlaceholderText"
            elseif instance:IsA("TextLabel") or instance:IsA("TextButton") then
                property = "Text"
            end
            if not property or instance:GetAttribute("TBLUserText") then
                return
            end
            local binding = { original = instance[property], rendered = nil, connections = {} }
            function binding.render()
                if not instance.Parent or instance:GetAttribute("TBLUserText") then
                    return
                end
                local value = self:translate(binding.original):gsub("%f[%w]TBL%f[%W]", "Zeen")
                binding.rendered = value
                if instance[property] ~= value then
                    instance[property] = value
                end
            end
            self.bindings[instance] = binding
            binding.connections[1] = instance:GetPropertyChangedSignal(property):Connect(function()
                local value = instance[property]
                if value == binding.rendered then
                    return
                end
                binding.original = value
                if self.locale ~= "en" or english[value] or value:find("TBL", 1, true) then
                    queue(binding)
                end
            end)
            binding.connections[2] = instance.Destroying:Connect(function()
                self.bindings[instance] = nil
                for _, connection in ipairs(binding.connections) do
                    connection:Disconnect()
                end
            end)
            binding.render()
        end
        local visited = 0
        local function walk(instance)
            if self.generation ~= generation then
                return
            end
            watch(instance)
            visited += 1
            if visited % 80 == 0 then
                task.wait()
            end
            for _, child in ipairs(instance:GetChildren()) do
                walk(child)
            end
        end
        self.connections[1] = root.DescendantAdded:Connect(watch)
        self.connections[2] = root.Destroying:Connect(function()
            self:detach()
        end)
        walk(root)
        for _, extra in ipairs(extras or {}) do
            self.connections[#self.connections + 1] = extra.DescendantAdded:Connect(watch)
            walk(extra)
        end
    end
    function Localization:detach()
        self.generation = (self.generation or 0) + 1
        for _, connection in ipairs(self.connections) do
            connection:Disconnect()
        end
        self.connections = {}
        for _, binding in pairs(self.bindings) do
            for _, connection in ipairs(binding.connections) do
                connection:Disconnect()
            end
        end
        self.bindings = {}
    end
    return Localization
end)()

-- Zeen interface based on the supplied zxszeen adapter.
local function createZeenUI()
    local Zeen=(function()
local Library={Version="0.3.0", Options={}}
function Library:CreateWindow(options)
options=options or {}
local cleanups={}
local windowOptions={}
local function onCleanup(fn) table.insert(cleanups,fn) end
local screen=Instance.new("ScreenGui")
screen.Name="ZeenUI"
screen.Enabled=true
screen.ResetOnSpawn=false
screen.DisplayOrder=0
screen.ZIndexBehavior=Enum.ZIndexBehavior.Sibling
screen.ScreenInsets=Enum.ScreenInsets.CoreUISafeInsets
local root=Instance.new("Frame")
root.Name="Frame"
root.Size=UDim2.new(0,681,0,430)
root.Position=UDim2.new(0.4656893312931061,0,0.5088235139846802,0)
root.AnchorPoint=Vector2.new(0.5,0.5)
root.BackgroundColor3=Color3.new(0.0470588244497776,0.0470588244497776,0.0470588244497776)
root.BackgroundTransparency=0
root.BorderSizePixel=0
root.Visible=true
root.Active=true
root.ZIndex=1
root.ClipsDescendants=false
root.Rotation=0
root.Parent=screen
local rootCorner=Instance.new("UICorner")
rootCorner.Name="UICorner"
rootCorner.CornerRadius=UDim.new(0,8)
rootCorner.Parent=root
local rootShadow=Instance.new("UIShadow")
rootShadow.Name="UIShadow"
rootShadow.Enabled=true
rootShadow.ZIndex=-1
rootShadow.BlurRadius=UDim.new(0,20)
rootShadow.Offset=UDim2.new(0,0,0,0)
rootShadow.ShowBehindParent=true
rootShadow.Color=Color3.new(0,0,0)
rootShadow.Transparency=0.5
rootShadow.Parent=root
local rootGradient=Instance.new("UIGradient")
rootGradient.Name="UIGradient"
rootGradient.Enabled=false
rootGradient.Scale=1
rootGradient.Offset=Vector2.new(0,0)
rootGradient.Color=ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(0.03529411926865578,0,0.05098039284348488)),ColorSequenceKeypoint.new(1,Color3.new(0.06666667014360428,0.06666667014360428,0.06666667014360428))})
rootGradient.Rotation=78
rootGradient.Parent=root
local windowTitle=Instance.new("TextLabel")
windowTitle.Name="TextLabel"
windowTitle.Size=UDim2.new(0,120,0,29)
windowTitle.Position=UDim2.new(0.008810572326183319,0,0.020930232480168343,0)
windowTitle.AnchorPoint=Vector2.new(0,0)
windowTitle.BackgroundColor3=Color3.new(1,1,1)
windowTitle.BackgroundTransparency=1
windowTitle.BorderSizePixel=0
windowTitle.Visible=true
windowTitle.Active=false
windowTitle.ZIndex=1
windowTitle.ClipsDescendants=false
windowTitle.Text="Zeen Hub"
windowTitle.TextSize=25
windowTitle.FontFace=Font.new("rbxasset://fonts/families/Roboto.json",Enum.FontWeight.Regular,Enum.FontStyle.Normal)
windowTitle.TextColor3=Color3.new(1,1,1)
windowTitle.TextTransparency=0
windowTitle.TextStrokeTransparency=1
windowTitle.TextXAlignment=Enum.TextXAlignment.Center
windowTitle.TextYAlignment=Enum.TextYAlignment.Center
windowTitle.Rotation=0
windowTitle.Parent=root
local windowSubtitle=Instance.new("TextLabel")
windowSubtitle.Name="TextLabel"
windowSubtitle.Size=UDim2.new(0,128,0,37)
windowSubtitle.Position=UDim2.new(-0.002936857519671321,0,0.055813953280448914,0)
windowSubtitle.AnchorPoint=Vector2.new(0,0)
windowSubtitle.BackgroundColor3=Color3.new(1,1,1)
windowSubtitle.BackgroundTransparency=1
windowSubtitle.BorderSizePixel=0
windowSubtitle.Visible=true
windowSubtitle.Active=false
windowSubtitle.ZIndex=1
windowSubtitle.ClipsDescendants=false
windowSubtitle.Text="Description"
windowSubtitle.TextSize=19
windowSubtitle.FontFace=Font.new("rbxasset://fonts/families/Roboto.json",Enum.FontWeight.Regular,Enum.FontStyle.Normal)
windowSubtitle.TextColor3=Color3.new(1,1,1)
windowSubtitle.TextTransparency=0.6200000047683716
windowSubtitle.TextStrokeTransparency=1
windowSubtitle.TextXAlignment=Enum.TextXAlignment.Center
windowSubtitle.TextYAlignment=Enum.TextYAlignment.Center
windowSubtitle.Rotation=0
windowSubtitle.Parent=root
local openingScale=Instance.new("UIScale")
openingScale.Name="OpeningScale"
openingScale.Scale=1
openingScale.Parent=root
local firstControl=Instance.new("TextButton")
firstControl.Name="Frame"
firstControl.Size=UDim2.new(0,12,0,21)
firstControl.Position=UDim2.new(0.9676945805549622,0,0.03953488543629646,0)
firstControl.AnchorPoint=Vector2.new(0,0)
firstControl.BackgroundColor3=Color3.new(1,1,1)
firstControl.BackgroundTransparency=0
firstControl.BorderSizePixel=0
firstControl.Visible=true
firstControl.Active=false
firstControl.ZIndex=1
firstControl.ClipsDescendants=false
firstControl.Rotation=0
firstControl.Name="Minimize"; firstControl.Text=""; firstControl.AutoButtonColor=false
firstControl.Parent=root
local firstCorner=Instance.new("UICorner")
firstCorner.Name="UICorner"
firstCorner.CornerRadius=UDim.new(0,8)
firstCorner.Parent=firstControl
local firstGradient=Instance.new("UIGradient")
firstGradient.Name="UIGradient"
firstGradient.Enabled=true
firstGradient.Scale=1
firstGradient.Offset=Vector2.new(0,0)
firstGradient.Color=ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(0.5686274766921997,0.5686274766921997,0.5686274766921997)),ColorSequenceKeypoint.new(1,Color3.new(0.7921568751335144,0.7921568751335144,0.7921568751335144))})
firstGradient.Rotation=0
firstGradient.Parent=firstControl
local secondControl=Instance.new("TextButton")
secondControl.Name="Frame"
secondControl.Size=UDim2.new(0,12,0,21)
secondControl.Position=UDim2.new(0.9412628412246704,0,0.03953488543629646,0)
secondControl.AnchorPoint=Vector2.new(0,0)
secondControl.BackgroundColor3=Color3.new(1,1,1)
secondControl.BackgroundTransparency=0
secondControl.BorderSizePixel=0
secondControl.Visible=true
secondControl.Active=false
secondControl.ZIndex=1
secondControl.ClipsDescendants=false
secondControl.Rotation=0
secondControl.Name="Minimize"; secondControl.Text=""; secondControl.AutoButtonColor=false
secondControl.Parent=root
local secondCorner=Instance.new("UICorner")
secondCorner.Name="UICorner"
secondCorner.CornerRadius=UDim.new(0,8)
secondCorner.Parent=secondControl
local secondGradient=Instance.new("UIGradient")
secondGradient.Name="UIGradient"
secondGradient.Enabled=true
secondGradient.Scale=1
secondGradient.Offset=Vector2.new(0,0)
secondGradient.Color=ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(0.5686274766921997,0.5686274766921997,0.5686274766921997)),ColorSequenceKeypoint.new(1,Color3.new(0.7921568751335144,0.7921568751335144,0.7921568751335144))})
secondGradient.Rotation=0
secondGradient.Parent=secondControl
local thirdControl=Instance.new("TextButton")
thirdControl.Name="Frame"
thirdControl.Size=UDim2.new(0,12,0,21)
thirdControl.Position=UDim2.new(0.9148311018943787,0,0.03953488543629646,0)
thirdControl.AnchorPoint=Vector2.new(0,0)
thirdControl.BackgroundColor3=Color3.new(1,1,1)
thirdControl.BackgroundTransparency=0
thirdControl.BorderSizePixel=0
thirdControl.Visible=true
thirdControl.Active=false
thirdControl.ZIndex=1
thirdControl.ClipsDescendants=false
thirdControl.Rotation=0
thirdControl.Name="Minimize"; thirdControl.Text=""; thirdControl.AutoButtonColor=false
thirdControl.Parent=root
local thirdCorner=Instance.new("UICorner")
thirdCorner.Name="UICorner"
thirdCorner.CornerRadius=UDim.new(0,8)
thirdCorner.Parent=thirdControl
local thirdGradient=Instance.new("UIGradient")
thirdGradient.Name="UIGradient"
thirdGradient.Enabled=true
thirdGradient.Scale=1
thirdGradient.Offset=Vector2.new(0,0)
thirdGradient.Color=ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(0.5686274766921997,0.5686274766921997,0.5686274766921997)),ColorSequenceKeypoint.new(1,Color3.new(0.7921568751335144,0.7921568751335144,0.7921568751335144))})
thirdGradient.Rotation=0
thirdGradient.Parent=thirdControl
local restoreBar=Instance.new("TextButton")
restoreBar.Name="RestoreSidebar"
restoreBar.Size=UDim2.new(0,8,0,100)
restoreBar.Position=UDim2.new(0,3,0.5,0)
restoreBar.AnchorPoint=Vector2.new(0,0.5)
restoreBar.BackgroundColor3=Color3.new(0.13725490868091583,0.13725490868091583,0.13725490868091583)
restoreBar.BackgroundTransparency=0.800000011920929
restoreBar.BorderSizePixel=0
restoreBar.Visible=false
restoreBar.Active=true
restoreBar.ZIndex=1
restoreBar.ClipsDescendants=false
restoreBar.Text=""
restoreBar.TextSize=8
restoreBar.FontFace=Font.new("rbxasset://fonts/families/LegacyArial.json",Enum.FontWeight.Regular,Enum.FontStyle.Normal)
restoreBar.TextColor3=Color3.new(0.10588236153125763,0.16470588743686676,0.20784315466880798)
restoreBar.TextTransparency=0.800000011920929
restoreBar.TextStrokeTransparency=1
restoreBar.TextXAlignment=Enum.TextXAlignment.Center
restoreBar.TextYAlignment=Enum.TextYAlignment.Center
restoreBar.Rotation=0
restoreBar.Parent=screen
local restoreCorner=Instance.new("UICorner")
restoreCorner.Name="UICorner"
restoreCorner.CornerRadius=UDim.new(1,0)
restoreCorner.Parent=restoreBar
local gui=screen
gui.Name="ScreenGui"
gui.Parent=game:GetService("Players").LocalPlayer:FindFirstChildOfClass("PlayerGui")
local controls = {}
for _, child in ipairs(gui.Frame:GetChildren()) do
 if child:IsA("TextButton") then table.insert(controls, child) end
end
table.sort(controls, function(a,b) return a.Position.X.Scale < b.Position.X.Scale end)
local names = {"Green", "Minimize", "Close"}
for i, child in ipairs(controls) do child.Name = names[i] end
for _, button in ipairs(controls) do
 button.Active = true
 button.Interactable = true
 button.ZIndex = 20
end
gui.Frame.Size=UDim2.new(0,681,0,430)
gui.Frame.Position=UDim2.new(0.49376168847084045,0,0.5,0)
gui.Frame.AnchorPoint=Vector2.new(0.5,0.5)
gui.Frame.BackgroundColor3=Color3.new(0.0470588244497776,0.0470588244497776,0.0470588244497776)
gui.Frame.BackgroundTransparency=0
for _,label in ipairs(gui.Frame:GetChildren()) do if label:IsA("TextLabel") and label.Text=="Zeen Hub" then
label.Position=UDim2.new(0.008810572326183319,0,0.020930232480168343,0)
label.Size=UDim2.new(0,120,0,29)
label.TextSize=25
label.FontFace=Font.new("rbxasset://fonts/families/Roboto.json",Enum.FontWeight.Medium,Enum.FontStyle.Normal)
label.TextColor3=Color3.new(1,1,1)
label.TextTransparency=0
label.TextXAlignment=Enum.TextXAlignment.Center
label.TextYAlignment=Enum.TextYAlignment.Center
end end
for _,label in ipairs(gui.Frame:GetChildren()) do if label:IsA("TextLabel") and label.Text=="Description" then
label.Position=UDim2.new(-0.010279001668095589,0,0.041000012308359146,0)
label.Size=UDim2.new(0,133,0,47)
label.TextSize=19
label.FontFace=Font.new("rbxasset://fonts/families/Roboto.json",Enum.FontWeight.Medium,Enum.FontStyle.Normal)
label.TextColor3=Color3.new(1,1,1)
label.TextTransparency=0.6200000047683716
label.TextXAlignment=Enum.TextXAlignment.Center
label.TextYAlignment=Enum.TextYAlignment.Center
end end
gui.Frame.Green.Size=UDim2.new(0,16,0,17)
gui.Frame.Green.Position=UDim2.new(0.890999972820282,0,0.04100000113248825,0)
gui.Frame.Green.AnchorPoint=Vector2.new(0,0)
gui.Frame.Green.BackgroundColor3=Color3.new(1,1,1)
gui.Frame.Green.BackgroundTransparency=0
gui.Frame.Green.UICorner.CornerRadius=UDim.new(0,8)
gui.Frame.Green.UIGradient.Color=ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(0.5686274766921997,0.5686274766921997,0.5686274766921997)),ColorSequenceKeypoint.new(1,Color3.new(0.7921568751335144,0.7921568751335144,0.7921568751335144))})
gui.Frame.Green.UIGradient.Rotation=0
gui.Frame.Green.UIGradient.Enabled=true
gui.Frame.Green.UIGradient.Offset=Vector2.new(0,0)
gui.Frame.Minimize.Size=UDim2.new(0,16,0,17)
gui.Frame.Minimize.Position=UDim2.new(0.9240000247955322,0,0.04100000113248825,0)
gui.Frame.Minimize.AnchorPoint=Vector2.new(0,0)
gui.Frame.Minimize.BackgroundColor3=Color3.new(1,1,1)
gui.Frame.Minimize.BackgroundTransparency=0
gui.Frame.Minimize.UICorner.CornerRadius=UDim.new(0,8)
gui.Frame.Minimize.UIGradient.Color=ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(0.5686274766921997,0.5686274766921997,0.5686274766921997)),ColorSequenceKeypoint.new(1,Color3.new(0.7921568751335144,0.7921568751335144,0.7921568751335144))})
gui.Frame.Minimize.UIGradient.Rotation=0
gui.Frame.Minimize.UIGradient.Enabled=true
gui.Frame.Minimize.UIGradient.Offset=Vector2.new(0,0)
gui.Frame.Close.Size=UDim2.new(0,16,0,17)
gui.Frame.Close.Position=UDim2.new(0.9559999704360962,0,0.04100000113248825,0)
gui.Frame.Close.AnchorPoint=Vector2.new(0,0)
gui.Frame.Close.BackgroundColor3=Color3.new(1,1,1)
gui.Frame.Close.BackgroundTransparency=0
gui.Frame.Close.UICorner.CornerRadius=UDim.new(0,8)
gui.Frame.Close.UIGradient.Color=ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(0.5686274766921997,0.5686274766921997,0.5686274766921997)),ColorSequenceKeypoint.new(1,Color3.new(0.7921568751335144,0.7921568751335144,0.7921568751335144))})
gui.Frame.Close.UIGradient.Rotation=0
gui.Frame.Close.UIGradient.Enabled=true
gui.Frame.Close.UIGradient.Offset=Vector2.new(0,0)
local frame=gui:WaitForChild("Frame")
for _,button in ipairs(controls) do
 button.Size=UDim2.fromOffset(13,14)
 local p=button.Position
 button.Position=UDim2.new(p.X.Scale,p.X.Offset+1.5,p.Y.Scale,p.Y.Offset+1.5)
 button.UICorner.CornerRadius=UDim.new(1,0)
end
for i,button in ipairs(controls) do
 button.Position=UDim2.new(1,-(32+(3-i)*18),0,19)
end
gui.RestoreSidebar.Size=UDim2.fromOffset(13,176)
gui.RestoreSidebar.Position=UDim2.new(0.003898939350619912,3,0.48676469922065737,0)
gui.RestoreSidebar.BackgroundColor3=Color3.new(1,1,1)
gui.RestoreSidebar.BackgroundTransparency=0.8
frame.Size=options.Size or frame.Size
frame.Position=options.Position or frame.Position
for _,label in ipairs(frame:GetChildren()) do
 if label:IsA("TextLabel") and label.Text=="Zeen Hub" then label.Text=options.Title or "Zeen Hub"
 elseif label:IsA("TextLabel") and label.Text=="Description" then label.Text=options.SubTitle or options.Description or "Description" end
end
local UIS=game:GetService("UserInputService")
local TS=game:GetService("TweenService")
local scale=frame:WaitForChild("OpeningScale")
local bar=gui:WaitForChild("RestoreSidebar")
local connections={}
local windowActions: {[string]: () -> ()}={}
local tweens={}
local alive=true
local function connect(signal,fn)
 local c=signal:Connect(fn)
 table.insert(connections,c)
 return c
end
local dragging,start,position,inputHeld
connect(frame.InputBegan,function(input)
 if input.UserInputType~=Enum.UserInputType.MouseButton1 and input.UserInputType~=Enum.UserInputType.Touch then return end
 if input.Position.Y>frame.AbsolutePosition.Y+70 then return end
 for _,button in ipairs(controls) do
  local p,s=button.AbsolutePosition,button.AbsoluteSize
  if input.Position.X>=p.X and input.Position.X<=p.X+s.X and input.Position.Y>=p.Y and input.Position.Y<=p.Y+s.Y then return end
 end
 dragging=true
 start=input.Position
 position=frame.Position
 inputHeld=input
end)
connect(UIS.InputChanged,function(input)
 if not dragging then return end
 if input~=inputHeld and input.UserInputType~=Enum.UserInputType.MouseMovement then return end
 local d=input.Position-start
 local size=gui.AbsoluteSize; local half=frame.AbsoluteSize/2
 local x=position.X.Scale*size.X+position.X.Offset+d.X
 local y=position.Y.Scale*size.Y+position.Y.Offset+d.Y
 frame.Position=UDim2.fromOffset(math.clamp(x,half.X+8,math.max(half.X+8,size.X-half.X-8)),math.clamp(y,half.Y+8,math.max(half.Y+8,size.Y-half.Y-8)))
end)
connect(UIS.InputEnded,function(input) if input==inputHeld then dragging=false end end)
local originals={}
for _,label in ipairs(frame:GetChildren()) do if label:IsA("TextLabel") and label.Text==(options.Title or "Zeen Hub") then label.Position=UDim2.new(0.41116005182266235,0,0.011627906933426857,6); label.Size=UDim2.fromOffset(120,29) end end
for _,label in ipairs(frame:GetChildren()) do if label:IsA("TextLabel") and label.Text==(options.SubTitle or options.Description or "Description") then label.Position=UDim2.new(0.40234947204589844,0,0.054953500628471375,6); label.Size=UDim2.fromOffset(133,28) end end
local logo=Instance.new("ImageLabel")
logo.Name="Logo"; logo.Image="rbxassetid://89606039691079"; logo.BackgroundTransparency=1
logo.Position=UDim2.fromScale(-0.005999997723847628,-0.020930232480168343); logo.Size=UDim2.fromOffset(78,79); logo.Parent=frame
local tabIcons={}
local tabPages={}
local tabTweens={}
local selectedTab=0
local tabPositions={}
local tabHandles={}
local componentHandles={}
local viewportOverride
local preferredSize=frame.Size
local rail=Instance.new("ScrollingFrame")
rail.Name="TabRail"; rail.BackgroundTransparency=1; rail.BorderSizePixel=0; rail.ScrollBarThickness=0
rail.Position=UDim2.fromOffset(0,70); rail.Size=UDim2.new(0,68,1,-82)
rail.CanvasSize=UDim2.new(); rail.Parent=frame
local function viewport()
 return viewportOverride or gui.AbsoluteSize
end
local function clampWindow()
 local size=viewport(); local half=frame.AbsoluteSize/2
 local center=Vector2.new(frame.Position.X.Scale*size.X+frame.Position.X.Offset,frame.Position.Y.Scale*size.Y+frame.Position.Y.Offset)
 frame.Position=UDim2.fromOffset(math.clamp(center.X,half.X+8,math.max(half.X+8,size.X-half.X-8)),math.clamp(center.Y,half.Y+8,math.max(half.Y+8,size.Y-half.Y-8)))
end
local function layoutResponsive()
 if not alive then return end
 local size=viewport()
 if size.X<1 or size.Y<1 then return end
 local width=math.min(preferredSize.X.Offset+preferredSize.X.Scale*size.X,size.X-24)
 local height=math.min(preferredSize.Y.Offset+preferredSize.Y.Scale*size.Y,size.Y-24)
 frame.Size=UDim2.fromOffset(math.max(240,width),math.max(180,height))
 local compact=width<570
 gui:SetAttribute("CompactLayout",compact)
 for _,tab in ipairs(tabHandles) do
  local page=tab.Page
  page.ScrollingEnabled=compact
  local left,right=tab.Left,tab.Right
  if compact then
   local lh=left.UIListLayout.AbsoluteContentSize.Y+16
   local rh=right.UIListLayout.AbsoluteContentSize.Y+16
   left.Position=UDim2.new(); left.Size=UDim2.new(1,0,0,lh)
   right.Position=UDim2.fromOffset(0,lh+10); right.Size=UDim2.new(1,0,0,rh)
   left.ScrollingEnabled=false; right.ScrollingEnabled=false
   page.CanvasSize=UDim2.fromOffset(0,lh+rh+10)
  else
   left.Position=UDim2.new(); right.Position=UDim2.new(.5,6,0,0)
   left.Size=UDim2.new(.5,-6,1,0); right.Size=left.Size
   left.ScrollingEnabled=true; right.ScrollingEnabled=true; page.CanvasSize=UDim2.new()
  end
  page.Divider.Visible=not compact
 end
 rail.CanvasSize=UDim2.fromOffset(0,#tabHandles*48+8)
 clampWindow()
end
connect(gui:GetPropertyChangedSignal("AbsoluteSize"),layoutResponsive)
local function selectTab(index, instant)
 if not tabIcons[index] then return end
 selectedTab=index
 for i,icon in ipairs(tabIcons) do
  if tabTweens[i] then tabTweens[i]:Cancel() end
  local opacity=i==index and 0 or 0.6
  local selected=i==index
  local targetSize=selected and UDim2.fromOffset(38,38) or UDim2.fromOffset(32,34)
  local shadow=icon:FindFirstChild("SelectedShadow")
  if originals[shadow] then originals[shadow].Transparency=selected and 0.78 or 1 end
  if instant then
   icon.Size=targetSize
   if shadow then shadow.Transparency=selected and 0.78 or 1 end
  else
   TS:Create(icon,TweenInfo.new(0.18,Enum.EasingStyle.Sine,Enum.EasingDirection.Out),{Size=targetSize}):Play()
   if shadow then TS:Create(shadow,TweenInfo.new(0.18),{Transparency=selected and 0.78 or 1}):Play() end
  end
  if originals and originals[icon] then originals[icon].ImageTransparency=opacity end
  if instant then icon.ImageTransparency=opacity else
   tabTweens[i]=TS:Create(icon,TweenInfo.new(0.18,Enum.EasingStyle.Sine,Enum.EasingDirection.Out),{ImageTransparency=opacity})
   tabTweens[i]:Play()
  end
  tabPages[i].Visible=i==index
 end
 gui:SetAttribute("SelectedTab",index)
end
local function addTab(options)
 options=options or {}
 local index=#tabIcons+1
 local icon=Instance.new("ImageButton")
 icon.Name="Tab"..index
 local asset=tostring(options.Icon or "111598016394173")
 icon.Image=string.find(asset,"rbxassetid://",1,true) and asset or "rbxassetid://"..asset
 icon.BackgroundTransparency=1
 icon.AutoButtonColor=false
 icon.Active=true
 icon.AnchorPoint=Vector2.new(0.5,0.5)
 icon.Position=UDim2.fromOffset(34,24+(index-1)*48)
 icon.Size=UDim2.fromOffset(32,34)
 local selectedShadow=Instance.new("UIShadow")
 selectedShadow.Name="SelectedShadow"
 selectedShadow.Color=Color3.new(1,1,1)
 selectedShadow.BlurRadius=UDim.new(0,20)
 selectedShadow.Transparency=1
 selectedShadow.Parent=icon
 originals[selectedShadow]={Transparency=1}
 icon.Parent=rail
 tabIcons[index]=icon
 tabPositions[index]=icon.Position
 local page=Instance.new("ScrollingFrame")
 page.BorderSizePixel=0; page.ScrollBarThickness=2; page.CanvasSize=UDim2.new(); page.ScrollingEnabled=false
 page.Name=options.Title or ("TabPage"..index)
 page.BackgroundTransparency=1
 page.Position=UDim2.fromOffset(78,76)
 page.Size=UDim2.new(1,-94,1,-92)
 page.Visible=false
 page.Parent=frame
 local columns={}
 for side=1,2 do
  local column=Instance.new("ScrollingFrame")
  column.Name=side==1 and "Left" or "Right"
  column.Position=UDim2.new(side==1 and 0 or 0.5,side==1 and 0 or 6,0,0)
  column.Size=UDim2.new(0.5,-6,1,0)
  column.BackgroundTransparency=1
  column.BorderSizePixel=0
  column.ScrollBarThickness=2
  column.CanvasSize=UDim2.new()
  column.AutomaticCanvasSize=Enum.AutomaticSize.Y
  column.Parent=page
  local padding=Instance.new("UIPadding")
  padding.PaddingTop=UDim.new(0,6)
  padding.PaddingLeft=UDim.new(0,4)
  padding.PaddingRight=UDim.new(0,4)
  padding.PaddingBottom=UDim.new(0,8)
  padding.Parent=column
  local layout=Instance.new("UIListLayout")
  layout.Padding=UDim.new(0,10)
  layout.SortOrder=Enum.SortOrder.LayoutOrder
  layout.Parent=column
  columns[column.Name]=column
 end
 tabPages[index]=page
 local tab={Title=options.Title or ("Tab "..index),Icon=icon,Page=page,Index=index}
 tab.Left=columns.Left
 tab.Right=columns.Right
 local divider=Instance.new("Frame")
 divider.Name="Divider"
 divider.Position=UDim2.new(0.5,0,0,4)
 divider.Size=UDim2.new(0,1,1,-8)
 divider.BackgroundColor3=Color3.fromRGB(35,35,35)
 divider.BackgroundTransparency=0.93
 divider.BorderSizePixel=0
 divider.Parent=page
 originals[divider]={BackgroundTransparency=0.93}
 function tab:AddToggle(id, config)
  if type(id) == "table" then config = id; id = nil end
  config = config or {}
  local row = Instance.new("TextButton")
  row.Name = id or "Toggle"
  row.Text = ""
  row.AutoButtonColor = false
  row.Active = true
  row.BackgroundColor3 = Color3.fromRGB(11,11,11)
  row.BackgroundTransparency = 0.18
  row.BorderSizePixel = 0
  row.Size = UDim2.new(1, 0, 0, 60)
  row.Parent = columns[config.Side or "Left"] or columns.Left
  local boxCorner=Instance.new("UICorner")
  boxCorner.CornerRadius=UDim.new(0,8)
  boxCorner.Parent=row
  local elevation=Instance.new("UIShadow")
  elevation.Color=Color3.fromRGB(72,72,72)
  elevation.Transparency=0.82
  elevation.BlurRadius=UDim.new(0,8)
  elevation.Offset=UDim2.fromOffset(0,2)
  elevation.Parent=row
  local outline=Instance.new("UIStroke")
  outline.Color=Color3.fromRGB(72,72,72)
  outline.Transparency=0.9
  outline.Thickness=1
  outline.Parent=row
  local title = Instance.new("TextLabel")
  title.Name = "Title"
  title.Text = config.Title or "Toggle"
  title.Font = Enum.Font.Roboto
  title.TextSize = 19
  title.TextColor3 = Color3.fromRGB(225, 225, 225)
  title.TextXAlignment = Enum.TextXAlignment.Left
  title.BackgroundTransparency = 1
  title.Position = UDim2.fromOffset(12,9)
  title.Size = UDim2.new(1, -72, 0, 22)
  title.TextTruncate = Enum.TextTruncate.AtEnd
  title.Parent = row
  local description=Instance.new("TextLabel")
  description.Name="Description"
  description.Text=config.Description or ""
  description.Font=Enum.Font.Roboto
  description.TextSize=16
  description.TextColor3=Color3.fromRGB(115,115,115)
  description.TextXAlignment=Enum.TextXAlignment.Left
  description.BackgroundTransparency=1
  description.Position=UDim2.fromOffset(12,29)
  description.Size=UDim2.new(1,-72,0,20)
  description.TextWrapped=true
  description.Parent=row
  local track = Instance.new("Frame")
  track.Name = "Track"
  track.AnchorPoint = Vector2.new(1, 0.5)
  track.Position = UDim2.new(1, -10, 0.5, 0)
  track.Size = UDim2.fromOffset(42, 24)
  track.BorderSizePixel = 0
  track.Parent = row
  local corner = Instance.new("UICorner")
  corner.CornerRadius = UDim.new(0, 12)
  corner.Parent = track
  local knob = Instance.new("Frame")
  knob.Name = "Knob"
  knob.Size = UDim2.fromOffset(18, 18)
  knob.Position = UDim2.fromOffset(3, 3)
  knob.BackgroundColor3 = Color3.new(1, 1, 1)
  knob.BorderSizePixel = 0
  knob.ZIndex = 3
  knob.Parent = track
  local knobCorner = Instance.new("UICorner")
  knobCorner.CornerRadius = UDim.new(1, 0)
  knobCorner.Parent = knob
  local shadow = Instance.new("UIShadow")
  shadow.Color = Color3.new(0, 0, 0)
  shadow.Transparency = 0.8
  shadow.BlurRadius = UDim.new(0, 5)
  shadow.Offset = UDim2.fromOffset(0, 2)
  shadow.Parent = knob
  local toggle = {Value = config.Default == true, Instance = row}
  local listeners = {}
  local toggleTweens = {}
  local function render(instant)
   for _, tween in ipairs(toggleTweens) do tween:Cancel() end
   toggleTweens = {}
   local color = toggle.Value and Color3.fromRGB(45, 45, 45) or Color3.fromRGB(18, 18, 18)
   local position = UDim2.fromOffset(toggle.Value and 21 or 3, 3)
   if instant then track.BackgroundColor3 = color; knob.Position = position; return end
   local info = TweenInfo.new(0.4, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut)
   local a = TS:Create(track, info, {BackgroundColor3 = color})
   local b = TS:Create(knob, info, {Position = position})
   toggleTweens = {a, b}
   a:Play()
   b:Play()
  end
  function toggle:SetValue(value,silent)
   if not alive then return end
   value = value == true
   if self.Value == value then return end
   self.Value = value
   render(false)
   if not silent then
    if config.Callback then config.Callback(value) end
    for _, callback in ipairs(listeners) do callback(value) end
   end
  end
  function toggle:OnChanged(callback) table.insert(listeners, callback); return self end
  function toggle:GetValue() return self.Value end
  connect(row.Activated, function() toggle:SetValue(not toggle.Value) end)
  onCleanup(function()
   for _, tween in ipairs(toggleTweens) do tween:Cancel() end
  end)
  originals[row] = {BackgroundTransparency = 0.18, TextTransparency = 0}
  originals[elevation] = {Transparency = 0.82}
  originals[outline] = {Transparency = 0.9}
  originals[description] = {BackgroundTransparency = 1, TextTransparency = 0, TextStrokeTransparency = 1}
  originals[title] = {BackgroundTransparency = 1, TextTransparency = 0, TextStrokeTransparency = 1}
  originals[track] = {BackgroundTransparency = 0}
  originals[knob] = {BackgroundTransparency = 0}
  originals[shadow] = {Transparency = 0.8}
  render(true)
  if id then Library.Options[id] = toggle end
  return toggle
 end
 function tab:AddButton(config)
  config=config or {}
  local row=Instance.new("TextButton")
  row.Name="Button"
  row.Text=""
  row.AutoButtonColor=false
  row.Active=true
  row.BorderSizePixel=0
  row.BackgroundColor3=Color3.fromRGB(11,11,11)
  row.BackgroundTransparency=0.18
  row.Size=UDim2.new(1,0,0,60)
  row.Parent=columns[config.Side or "Left"] or columns.Left
  local corner=Instance.new("UICorner")
  corner.CornerRadius=UDim.new(0,8)
  corner.Parent=row
  local shadow=Instance.new("UIShadow")
  shadow.Color=Color3.fromRGB(72,72,72)
  shadow.Transparency=0.82
  shadow.BlurRadius=UDim.new(0,8)
  shadow.Offset=UDim2.fromOffset(0,2)
  shadow.Parent=row
  local stroke=Instance.new("UIStroke")
  stroke.Color=Color3.fromRGB(72,72,72)
  stroke.Transparency=0.9
  stroke.Parent=row
  local title=Instance.new("TextLabel")
  title.Name="Title"
  title.Text=config.Title or "Button"
  title.Font=Enum.Font.Roboto
  title.TextSize=19
  title.TextColor3=Color3.fromRGB(225,225,225)
  title.TextXAlignment=Enum.TextXAlignment.Left
  title.BackgroundTransparency=1
  title.Position=UDim2.fromOffset(12,9)
  title.Size=UDim2.new(1,-48,0,22)
  title.Parent=row
  local description=Instance.new("TextLabel")
  description.Name="Description"
  description.Text=config.Description or ""
  description.Font=Enum.Font.Roboto
  description.TextSize=16
  description.TextColor3=Color3.fromRGB(115,115,115)
  description.TextXAlignment=Enum.TextXAlignment.Left
  description.BackgroundTransparency=1
  description.Position=UDim2.fromOffset(12,29)
  description.Size=UDim2.new(1,-48,0,20)
  description.TextTruncate=Enum.TextTruncate.AtEnd
  description.Parent=row
  local arrow=Instance.new("TextLabel")
  arrow.Name="Action"
  arrow.Text="›"
  arrow.Font=Enum.Font.Roboto
  arrow.TextSize=24
  arrow.TextColor3=Color3.fromRGB(140,140,140)
  arrow.BackgroundTransparency=1
  arrow.Position=UDim2.new(1,-34,0,0)
  arrow.Size=UDim2.new(0,24,1,0)
  arrow.Parent=row
  local hoverTween
  local function shade(color)
   if hoverTween then hoverTween:Cancel() end
   hoverTween=TS:Create(row,TweenInfo.new(0.15,Enum.EasingStyle.Sine),{BackgroundColor3=color})
   hoverTween:Play()
  end
  connect(row.MouseEnter,function() shade(Color3.fromRGB(20,20,20)) end)
  connect(row.MouseLeave,function() shade(Color3.fromRGB(11,11,11)) end)
  connect(row.MouseButton1Down,function() shade(Color3.fromRGB(7,7,7)) end)
  connect(row.MouseButton1Up,function() shade(Color3.fromRGB(20,20,20)) end)
  connect(row.Activated,function() if config.Callback then config.Callback() end end)
  onCleanup(function() if hoverTween then hoverTween:Cancel() end end)
  originals[row]={BackgroundTransparency=0.18,TextTransparency=0}
  originals[shadow]={Transparency=0.82}
  originals[stroke]={Transparency=0.9}
  for _,label in ipairs({title,description,arrow}) do originals[label]={BackgroundTransparency=1,TextTransparency=0,TextStrokeTransparency=1} end
  return {Instance=row}
 end
 function tab:AddSlider(id,config)
  if type(id)=="table" then config=id; id=nil end
  config=config or {}
  local minimum=config.Min or 0
  local maximum=config.Max or 100
  assert(maximum>minimum,"Slider Max must be greater than Min")
  local digits=config.Rounding or 0
  local factor=10^digits
  local row=Instance.new("Frame")
  row.Name=id or "Slider"
  row.Size=UDim2.new(1,0,0,60)
  row.BackgroundColor3=Color3.fromRGB(11,11,11)
  row.BackgroundTransparency=0.18
  row.BorderSizePixel=0
  row.Parent=columns[config.Side or "Left"] or columns.Left
  local corner=Instance.new("UICorner"); corner.CornerRadius=UDim.new(0,8); corner.Parent=row
  local shadow=Instance.new("UIShadow"); shadow.Color=Color3.fromRGB(72,72,72); shadow.Transparency=0.82; shadow.BlurRadius=UDim.new(0,8); shadow.Offset=UDim2.fromOffset(0,2); shadow.Parent=row
  local stroke=Instance.new("UIStroke"); stroke.Color=Color3.fromRGB(72,72,72); stroke.Transparency=0.9; stroke.Parent=row
  local title=Instance.new("TextLabel")
  title.Name="Title"; title.Text=config.Title or "Slider"; title.Font=Enum.Font.Roboto; title.TextSize=19
  title.TextColor3=Color3.fromRGB(225,225,225); title.BackgroundTransparency=1; title.TextXAlignment=Enum.TextXAlignment.Left
  title.Position=UDim2.fromOffset(12,10); title.Size=UDim2.new(0.45,-12,0,22); title.TextTruncate=Enum.TextTruncate.AtEnd; title.Parent=row
  local description=title:Clone()
  description.Name="Description"; description.Text=config.Description or ""; description.TextSize=16
  description.TextColor3=Color3.fromRGB(115,115,115); description.Position=UDim2.fromOffset(12,29); description.Size=UDim2.new(0.45,-12,0,18); description.Parent=row
  local input=Instance.new("TextBox")
  input.Name="Value"; input.Size=UDim2.fromOffset(42,26); input.AnchorPoint=Vector2.new(1,0.5)
  input.Position=UDim2.new(1,-10,0.5,0); input.BackgroundTransparency=1; input.BorderSizePixel=0
  input.TextColor3=Color3.fromRGB(200,200,200); input.Font=Enum.Font.Roboto; input.TextSize=15; input.ClearTextOnFocus=false; input.Parent=row
  local hit=Instance.new("TextButton")
  hit.Name="SliderTrack"; hit.Text=""; hit.AutoButtonColor=false; hit.BackgroundTransparency=1; hit.Active=true
  hit.Position=UDim2.new(0.55,6,0.5,-22); hit.Size=UDim2.new(0.45,-68,0,44); hit.Parent=row
  local track=Instance.new("Frame")
  track.Name="Track"; track.Size=UDim2.new(1,0,0,8); track.Position=UDim2.new(0,0,0.5,-4); track.BackgroundColor3=Color3.fromRGB(35,35,35); track.BorderSizePixel=0; track.Parent=hit
  local round=Instance.new("UICorner"); round.CornerRadius=UDim.new(1,0); round.Parent=track
  local fill=track:Clone(); fill.Name="Fill"; fill.Position=UDim2.new(); fill.BackgroundColor3=Color3.fromRGB(190,190,190); fill.Parent=track
  local knob=Instance.new("Frame")
  knob.Name="Knob"; knob.AnchorPoint=Vector2.new(0.5,0.5); knob.Size=UDim2.fromOffset(14,14); knob.BackgroundColor3=Color3.fromRGB(235,235,235); knob.BorderSizePixel=0; knob.Parent=track
  local knobCorner=Instance.new("UICorner"); knobCorner.CornerRadius=UDim.new(1,0); knobCorner.Parent=knob
  local slider={Value=minimum,Instance=row}
  local listeners={}
  local sliderDragging=false
  local touch
  local function render()
   local fraction=(slider.Value-minimum)/(maximum-minimum)
   fill.Size=UDim2.new(fraction,0,1,0)
   knob.Position=UDim2.new(fraction,0,0.5,0)
   input.Text=tostring(slider.Value)
  end
  function slider:SetValue(value,silent)
   if not alive then return end
   value=tonumber(value)
   if not value or value~=value then render(); return end
   value=math.clamp(math.floor(value*factor+0.5)/factor,minimum,maximum)
   local changed=self.Value~=value
   self.Value=value; render()
   if changed and not silent then
    if config.Callback then config.Callback(value) end
    for _,callback in ipairs(listeners) do callback(value) end
   end
  end
  function slider:OnChanged(callback) table.insert(listeners,callback); return self end
  function slider:GetValue() return self.Value end
  function slider:SetRange(low,high)
   assert(type(low)=="number" and type(high)=="number" and low==low and high==high and high>low,"Invalid slider range")
   minimum=low; maximum=high; self:SetValue(self.Value); render(); return self
  end
  function slider:SetRounding(value)
   digits=math.clamp(math.floor(tonumber(value) or 0),0,6); factor=10^digits; self:SetValue(self.Value); return self
  end
  local function move(x)
   if track.AbsoluteSize.X<=0 then return end
   slider:SetValue(minimum+math.clamp((x-track.AbsolutePosition.X)/track.AbsoluteSize.X,0,1)*(maximum-minimum))
  end
  connect(hit.InputBegan,function(inputObject)
   if inputObject.UserInputType~=Enum.UserInputType.MouseButton1 and inputObject.UserInputType~=Enum.UserInputType.Touch then return end
   if row:GetAttribute("Disabled") then return end
   sliderDragging=true; row.Parent.ScrollingEnabled=false; page.ScrollingEnabled=false; touch=inputObject; move(inputObject.Position.X)
  end)
  connect(UIS.InputChanged,function(inputObject)
   if sliderDragging and not row:GetAttribute("Disabled") and (inputObject==touch or inputObject.UserInputType==Enum.UserInputType.MouseMovement) then move(inputObject.Position.X) end
  end)
  connect(UIS.InputEnded,function(inputObject) if inputObject==touch then sliderDragging=false; if row.Parent then row.Parent.ScrollingEnabled=not gui:GetAttribute("CompactLayout"); page.ScrollingEnabled=gui:GetAttribute("CompactLayout")==true end end end)
  connect(input.FocusLost,function() slider:SetValue(input.Text) end)
  for _,object in ipairs(row:GetDescendants()) do
   local properties={}
   if object:IsA("GuiObject") then properties.BackgroundTransparency=object.BackgroundTransparency end
   if object:IsA("TextLabel") or object:IsA("TextButton") or object:IsA("TextBox") then properties.TextTransparency=object.TextTransparency; properties.TextStrokeTransparency=object.TextStrokeTransparency end
   if object:IsA("UIStroke") or object.ClassName=="UIShadow" then properties.Transparency=object.Transparency end
   if next(properties) then originals[object]=properties end
  end
  originals[row]={BackgroundTransparency=0.18}
  slider:SetValue(config.Default or minimum,true)
  if id then Library.Options[id]=slider end
  return slider
 end
 function tab:AddDropdown(id, config)
  if type(id)=="table" then config=id; id=nil end
  config=config or {}
  local multi=config.Multi==true
  local dropdown={Value=multi and {} or nil,Values={},Destroyed=false}
  local listeners={}
  local open=false
  local row=Instance.new("Frame")
  row.Name=id or "Dropdown"; row.Size=UDim2.new(1,0,0,60)
  row.BackgroundColor3=Color3.fromRGB(11,11,11); row.BackgroundTransparency=0.18
  row.BorderSizePixel=0; row.Parent=columns[config.Side or "Left"] or columns.Left
  dropdown.Instance=row
  local corner=Instance.new("UICorner"); corner.CornerRadius=UDim.new(0,8); corner.Parent=row
  local shadow=Instance.new("UIShadow"); shadow.Color=Color3.fromRGB(72,72,72); shadow.Transparency=0.82; shadow.BlurRadius=UDim.new(0,8); shadow.Offset=UDim2.fromOffset(0,2); shadow.Parent=row
  local title=Instance.new("TextLabel")
  title.Name="Title"; title.Text=config.Title or "Dropdown"; title.Font=Enum.Font.Roboto; title.TextSize=19
  title.TextColor3=Color3.fromRGB(225,225,225); title.BackgroundTransparency=1; title.TextXAlignment=Enum.TextXAlignment.Left
  title.Position=UDim2.fromOffset(12,9); title.Size=UDim2.new(0.48,-12,0,22); title.TextTruncate=Enum.TextTruncate.AtEnd; title.Parent=row
  local desc=title:Clone(); desc.Name="Description"; desc.Text=config.Description or ""; desc.TextSize=16
  desc.TextColor3=Color3.fromRGB(115,115,115); desc.Position=UDim2.fromOffset(12,29); desc.Size=UDim2.new(0.48,-12,0,20); desc.Parent=row
  local selector=Instance.new("TextButton")
  selector.Name="Selection"; selector.Text="Select"; selector.Font=Enum.Font.Roboto; selector.TextSize=14
  selector.TextColor3=Color3.fromRGB(190,190,190); selector.BackgroundTransparency=1; selector.AutoButtonColor=false
  selector.Position=UDim2.new(0.48,4,0,10); selector.Size=UDim2.new(0.52,-30,0,40)
  selector.TextTruncate=Enum.TextTruncate.AtEnd; selector.Parent=row
  selector.Size=UDim2.new(0.52,-14,0,40)
  selector.Active=false
  selector.Interactable=false
  local header=Instance.new("TextButton")
  header.Name="HeaderHitArea"
  header.Text=""
  header.BackgroundTransparency=1
  header.AutoButtonColor=false
  header.Active=true
  header.Size=UDim2.new(1,0,0,60)
  header.ZIndex=10
  header.Parent=row
  local panel=Instance.new("Frame")
  panel.Name="Options"; panel.BackgroundTransparency=1; panel.Position=UDim2.fromOffset(10,62); panel.Size=UDim2.new(1,-20,0,150); panel.Visible=false; panel.Parent=row
  local search=Instance.new("TextBox")
  search.Name="Search"; search.PlaceholderText="Search options"; search.Text=""; search.ClearTextOnFocus=false
  search.Font=Enum.Font.Roboto; search.TextSize=14; search.TextColor3=Color3.fromRGB(200,200,200)
  search.BackgroundTransparency=1; search.Size=UDim2.new(1,0,0,28); search.Parent=panel
  local list=Instance.new("ScrollingFrame")
  list.Name="List"; list.BackgroundTransparency=1; list.BorderSizePixel=0; list.ScrollBarThickness=2
  list.Position=UDim2.fromOffset(0,30); list.Size=UDim2.new(1,0,1,-30)
  list.CanvasSize=UDim2.new(); list.AutomaticCanvasSize=Enum.AutomaticSize.Y; list.Parent=panel
  local layout=Instance.new("UIListLayout"); layout.Padding=UDim.new(0,3); layout.Parent=list
  row.ClipsDescendants=true
  local optionRows={}
  local openTweens={}
  local openVersion=0
  local selectionTween
  local function fadeText(object,target)
   local tween=TS:Create(object,TweenInfo.new(0.18,Enum.EasingStyle.Sine,Enum.EasingDirection.Out),{TextTransparency=target})
   table.insert(openTweens,tween)
   tween:Play()
  end
  local function snapshot(value)
   if type(value)~="table" then return value end
   local copy={}; for key,v in pairs(value) do copy[key]=v end; return copy
  end
  local function equal(a,b)
   if type(a)~="table" or type(b)~="table" then return a==b end
   for k,v in pairs(a) do if b[k]~=v then return false end end
   for k,v in pairs(b) do if a[k]~=v then return false end end
   return true
  end
  local function selected(value) return multi and dropdown.Value[value]==true or (not multi and dropdown.Value==value) end
  local function render()
   local names={}
   for _,value in ipairs(dropdown.Values) do if selected(value) then table.insert(names,tostring(value)) end end
   selector.Text=#names>0 and table.concat(names,", ") or (config.Placeholder or "Select")
   for _,item in ipairs(optionRows) do
    item.Button.Text="  "..tostring(item.Value)
    if item.Tween then item.Tween:Cancel() end
    local isSelected=selected(item.Value)
    local background=isSelected and 0.72 or 1
    if originals[item.Button] then originals[item.Button].BackgroundTransparency=background end
    item.Tween=TS:Create(item.Button,TweenInfo.new(0.18,Enum.EasingStyle.Sine,Enum.EasingDirection.Out),{
     TextColor3=isSelected and Color3.fromRGB(235,235,235) or Color3.fromRGB(135,135,135),
     BackgroundTransparency=background,
    })
    item.Tween:Play()
   end
  end
  function dropdown:SetValue(value,silent)
   if self.Destroyed or not alive then return end
   local nextValue
   if multi then
    nextValue={}
    if type(value)=="table" then
     for _,option in ipairs(self.Values) do
      if value[option]==true or table.find(value,option) then nextValue[option]=true end
     end
    end
   elseif table.find(self.Values,value) then nextValue=value end
   local changed=not equal(self.Value,nextValue)
   self.Value=nextValue; render()
   if changed and not silent then
    if selectionTween then selectionTween:Cancel() end
    selector.TextColor3=Color3.fromRGB(245,245,245)
    selectionTween=TS:Create(selector,TweenInfo.new(0.25),{TextColor3=Color3.fromRGB(190,190,190)})
    selectionTween:Play()
   end
   if changed and not silent then
    if config.Callback then config.Callback(snapshot(self.Value)) end
    for _,callback in ipairs(listeners) do callback(snapshot(self.Value)) end
   end
  end
  function dropdown:GetValue() return snapshot(self.Value) end
  function dropdown:OnChanged(callback) table.insert(listeners,callback); return self end
  local function setOpen(value)
   if dropdown.Destroyed or not alive or open==value then return end
   open=value
   openVersion=openVersion+1
   local version=openVersion
   for _,tween in ipairs(openTweens) do tween:Cancel() end
   openTweens={}
   panel.Visible=true
   if value then
    search.TextTransparency=1
    for _,item in ipairs(optionRows) do item.Button.TextTransparency=1 end
   end
   fadeText(search,value and 0 or 1)
   for _,item in ipairs(optionRows) do fadeText(item.Button,value and 0 or 1) end
   local tween=TS:Create(row,TweenInfo.new(0.24,Enum.EasingStyle.Sine,Enum.EasingDirection.InOut),{Size=UDim2.new(1,0,0,value and 222 or 60)})
   table.insert(openTweens,tween)
   local connection
   connection=connect(tween.Completed,function(status)
    connection:Disconnect()
    if status==Enum.PlaybackState.Completed and version==openVersion and alive then panel.Visible=value end
   end)
   tween:Play()
  end
  local function rebuild()
   for _,item in ipairs(optionRows) do
    item.Connection:Disconnect(); if item.Tween then item.Tween:Cancel() end; originals[item.Button]=nil; item.Button:Destroy()
   end
   optionRows={}
   local query=string.lower(search.Text)
   for _,value in ipairs(dropdown.Values) do
    if string.find(string.lower(tostring(value)),query,1,true) then
     local button=Instance.new("TextButton")
     button.Font=Enum.Font.Roboto; button.TextSize=14; button.TextXAlignment=Enum.TextXAlignment.Left
     button.BackgroundTransparency=1; button.AutoButtonColor=false; button.Size=UDim2.new(1,-4,0,UIS.TouchEnabled and 44 or 26); button.Parent=list
     button.BackgroundColor3=Color3.fromRGB(40,40,40)
     button.BorderSizePixel=0
     local optionCorner=Instance.new("UICorner")
     optionCorner.CornerRadius=UDim.new(0,5)
     optionCorner.Parent=button
     local connection=button.Activated:Connect(function()
      if dropdown.Destroyed or row:GetAttribute("Disabled") then return end
      if multi then local nextValue=dropdown:GetValue(); nextValue[value]=not nextValue[value]; dropdown:SetValue(nextValue)
      else dropdown:SetValue(value); setOpen(false) end
     end)
     originals[button]={BackgroundTransparency=1,TextTransparency=0,TextStrokeTransparency=1}
     table.insert(optionRows,{Button=button,Value=value,Connection=connection})
    end
   end
   render()
  end
  function dropdown:SetValues(values)
   assert(type(values)=="table","Dropdown values must be a list")
   local cleaned={}
   for _,value in ipairs(values) do
    assert(type(value)=="string" or type(value)=="number","Options must be strings or numbers")
    if not table.find(cleaned,value) then table.insert(cleaned,value) end
   end
   local same=#cleaned==#self.Values
   if same then for i,value in ipairs(cleaned) do if self.Values[i]~=value then same=false; break end end end
   if same then render(); return self end
   self.Values=cleaned
   self:SetValue(self.Value)
   rebuild()
   return self
  end
  dropdown.SetOptions=dropdown.SetValues
  function dropdown:Refresh()
   if self.Destroyed or not alive then return false end
   if type(config.OptionsProvider)~="function" then return true end
   local ok,values=pcall(config.OptionsProvider)
   if not ok or type(values)~="table" then
    self.LastError=tostring(values); return false
   end
   self.LastError=nil; self:SetValues(values); return true
  end
  function dropdown:SetOpen(value) setOpen(value==true) end
  connect(header.Activated,function() setOpen(not open) end)
  connect(search:GetPropertyChangedSignal("Text"),rebuild)
  onCleanup(function()
   dropdown.Destroyed=true
   openVersion=openVersion+1
   for _,tween in ipairs(openTweens) do tween:Cancel() end
   if selectionTween then selectionTween:Cancel() end
   for _,item in ipairs(optionRows) do item.Connection:Disconnect(); if item.Tween then item.Tween:Cancel() end end
  end)
  for _,object in ipairs(row:GetDescendants()) do
   local properties={}
   if object:IsA("GuiObject") then properties.BackgroundTransparency=object.BackgroundTransparency end
   if object:IsA("TextLabel") or object:IsA("TextButton") or object:IsA("TextBox") then properties.TextTransparency=object.TextTransparency; properties.TextStrokeTransparency=object.TextStrokeTransparency end
   if object.ClassName=="UIShadow" then properties.Transparency=object.Transparency end
   if next(properties) then originals[object]=properties end
  end
  originals[row]={BackgroundTransparency=0.18}
  dropdown:SetValues(config.Values or config.Options or {})
  dropdown:Refresh()
  local default=config.Default
  if not multi and type(default)=="number" and dropdown.Values[default] then default=dropdown.Values[default] end
  dropdown:SetValue(default,true)
  local function autoRefresh()
   task.delay(math.max(0.5,config.RefreshInterval or 3),function()
    if not alive or dropdown.Destroyed then return end
    dropdown:Refresh()
    autoRefresh()
   end)
  end
  if config.AutoReload and type(config.OptionsProvider)=="function" then autoRefresh() end
  if id then Library.Options[id]=dropdown end
  return dropdown
 end
 function tab:AddInput(id,config)
  if type(id)=="table" then config=id; id=nil end
  config=config or {}
  local row=Instance.new("Frame")
  row.Name=id or "Input"; row.Size=UDim2.new(1,0,0,60)
  row.BackgroundColor3=Color3.fromRGB(11,11,11); row.BackgroundTransparency=0.18; row.BorderSizePixel=0
  row.Parent=columns[config.Side or "Left"] or columns.Left
  local corner=Instance.new("UICorner"); corner.CornerRadius=UDim.new(0,8); corner.Parent=row
  local shadow=Instance.new("UIShadow"); shadow.Color=Color3.fromRGB(72,72,72); shadow.Transparency=0.82; shadow.BlurRadius=UDim.new(0,8); shadow.Offset=UDim2.fromOffset(0,2); shadow.Parent=row
  local outline=Instance.new("UIStroke"); outline.Color=Color3.fromRGB(72,72,72); outline.Transparency=0.9; outline.Parent=row
  local title=Instance.new("TextLabel")
  title.Name="Title"; title.Text=config.Title or "Input"; title.Font=Enum.Font.Roboto; title.TextSize=19
  title.TextColor3=Color3.fromRGB(225,225,225); title.BackgroundTransparency=1; title.TextXAlignment=Enum.TextXAlignment.Left
  title.Position=UDim2.fromOffset(12,9); title.Size=UDim2.new(0.48,-12,0,22); title.TextTruncate=Enum.TextTruncate.AtEnd; title.Parent=row
  local description=title:Clone()
  description.Name="Description"; description.Text=config.Description or ""; description.TextSize=16
  description.TextColor3=Color3.fromRGB(115,115,115); description.Position=UDim2.fromOffset(12,29); description.Size=UDim2.new(0.48,-12,0,20); description.Parent=row
  local box=Instance.new("TextBox")
  box.Name="TextBox"; box.BackgroundTransparency=1; box.ClearTextOnFocus=false
  box.Font=Enum.Font.Roboto; box.TextSize=15; box.TextColor3=Color3.fromRGB(205,205,205)
  box.PlaceholderColor3=Color3.fromRGB(95,95,95); box.PlaceholderText=config.Placeholder or "Type here"
  box.Position=UDim2.new(0.48,8,0,12); box.Size=UDim2.new(0.52,-20,0,36)
  box.TextXAlignment=Enum.TextXAlignment.Center; box.TextTruncate=Enum.TextTruncate.AtEnd
  box.Text=tostring(config.Default or ""); box.Parent=row
  local control={Value=box.Text,Instance=row}
  local listeners={}
  local changing=false
  local focusTween
  local lastEmitted=control.Value
  local function emit()
   if control.Value==lastEmitted then return end
   lastEmitted=control.Value
   if config.Callback then config.Callback(control.Value) end
   for _,callback in ipairs(listeners) do callback(control.Value) end
  end
  local function valid(text)
   if config.Numeric and text~="" and tonumber(text)==nil then return false end
   return not config.MaxLength or #text<=config.MaxLength
  end
  function control:SetValue(value,silent)
   if not alive then return false end
   value=tostring(value or "")
   if not valid(value) then return false end
   changing=true; self.Value=value; box.Text=value; changing=false
   if silent then lastEmitted=value else emit() end
   return true
  end
  function control:GetValue() return self.Value end
  function control:OnChanged(callback) table.insert(listeners,callback); return self end
  local function focus(active)
   if focusTween then focusTween:Cancel() end
   focusTween=TS:Create(outline,TweenInfo.new(0.18),{Transparency=active and 0.5 or 0.9})
   originals[outline].Transparency=active and 0.5 or 0.9
   focusTween:Play()
  end
  connect(box.Focused,function() focus(true) end)
  connect(box.FocusLost,function() focus(false); if config.Finished then emit() end end)
  connect(box:GetPropertyChangedSignal("Text"),function()
   if changing then return end
   if config.MaxLength and #box.Text>config.MaxLength then changing=true; box.Text=string.sub(box.Text,1,config.MaxLength); changing=false end
   if not config.Numeric then
    control.Value=box.Text
    if not config.Finished then emit() end
   elseif tonumber(box.Text) or box.Text=="" then
    control.Value=box.Text
    if not config.Finished then emit() end
   end
  end)
  connect(box.FocusLost,function()
   if config.Numeric and not valid(box.Text) then changing=true; box.Text=control.Value; changing=false end
  end)
  onCleanup(function() if focusTween then focusTween:Cancel() end end)
  for _,object in ipairs(row:GetDescendants()) do
   local props={}
   if object:IsA("GuiObject") then props.BackgroundTransparency=object.BackgroundTransparency end
   if object:IsA("TextLabel") or object:IsA("TextBox") then props.TextTransparency=object.TextTransparency; props.TextStrokeTransparency=object.TextStrokeTransparency end
   if object:IsA("UIStroke") or object.ClassName=="UIShadow" then props.Transparency=object.Transparency end
   if next(props) then originals[object]=props end
  end
  originals[row]={BackgroundTransparency=0.18}
  if id then Library.Options[id]=control end
  return control
 end
 tab.Components={}
 for _,methodName in ipairs({"AddToggle","AddButton","AddSlider","AddDropdown","AddInput"}) do
  local factory=tab[methodName]
  tab[methodName]=function(self,id,config)
   local key=type(id)=="string" and id or nil
   local settings=type(id)=="table" and id or config or {}
   settings=table.clone(settings)
   local firstConnection=#connections+1
   local firstCleanup=#cleanups+1
   local control=methodName=="AddButton" and factory(self,settings) or factory(self,key,settings)
   local row=control.Instance
   local lastConnection=#connections
   local lastCleanup=#cleanups
   if settings.Callback then assert(type(settings.Callback)=="function","Callback must be a function") end
   control.Type=string.sub(methodName,4); control.Id=key; control.Enabled=true; control.Destroyed=false
   function control:SetTitle(value) local label=row:FindFirstChild("Title"); if label then label.Text=tostring(value) end; return self end
   function control:SetDescription(value) local label=row:FindFirstChild("Description"); if label then label.Text=tostring(value) end; return self end
   function control:SetVisible(value) row.Visible=value==true; layoutResponsive(); return self end
   function control:SetCallback(callback) assert(callback==nil or type(callback)=="function","Callback must be a function"); settings.Callback=callback; return self end
   function control:SetEnabled(value)
    self.Enabled=value==true; row:SetAttribute("Disabled",not self.Enabled)
    local objects=row:GetDescendants(); table.insert(objects,row)
    for _,object in ipairs(objects) do
     if object:IsA("GuiButton") then object.Interactable=self.Enabled end
     if object:IsA("TextBox") then object.TextEditable=self.Enabled; if not self.Enabled then object:ReleaseFocus() end end
    end
    return self
   end
   function control:SetSide(side) assert(side=="Left" or side=="Right","Invalid side"); row.Parent=columns[side]; layoutResponsive(); return self end
   function control:SetOrder(order) row.LayoutOrder=order; return self end
   function control:Destroy()
    if self.Destroyed then return end
    self.Destroyed=true
    for i=firstConnection,lastConnection do connections[i]:Disconnect() end
    for i=firstCleanup,lastCleanup do pcall(cleanups[i]) end
    local objects=row:GetDescendants(); table.insert(objects,row)
    for _,object in ipairs(objects) do originals[object]=nil end
    if key and Library.Options[key]==self then Library.Options[key]=nil end
    if key and windowOptions[key]==self then windowOptions[key]=nil end
    row:Destroy(); layoutResponsive()
   end
   if methodName=="AddButton" then
    function control:Fire(...) if not self.Destroyed and self.Enabled and settings.Callback then settings.Callback(...) end; return self end
   end
   if methodName=="AddInput" then
    function control:SetPlaceholder(value) row.TextBox.PlaceholderText=tostring(value); return self end
    function control:Focus() if self.Enabled and not self.Destroyed then row.TextBox:CaptureFocus() end; return self end
    function control:ReleaseFocus() row.TextBox:ReleaseFocus(); return self end
   end
   if methodName=="AddDropdown" then
    function control:GetOptions() return table.clone(self.Values) end
    function control:Open() if self.Enabled then self:SetOpen(true) end; return self end
    function control:Close() self:SetOpen(false); return self end
   end
   if control.SetValue then
    local setValue=control.SetValue
    control.SetValue=function(self,...) if self.Destroyed then return false end; return setValue(self,...) end
   end
   if control.OnChanged then
    local subscribe=control.OnChanged
    function control:ConnectChanged(callback)
     assert(type(callback)=="function","Callback must be a function")
     local connection={Connected=true}
     function connection:Disconnect() self.Connected=false end
     subscribe(self,function(...) if connection.Connected and not self.Destroyed then callback(...) end end)
     return connection
    end
   end
   table.insert(tab.Components,control); table.insert(componentHandles,control)
   if key then Library.Options[key]=control; windowOptions[key]=control end
   if settings.Enabled==false then control:SetEnabled(false) end
   if settings.Visible==false then control:SetVisible(false) end
   layoutResponsive()
   return control
  end
 end
 function tab:SetTitle(value) self.Title=tostring(value); self.Page.Name=self.Title; return self end
 function tab:SetIcon(value) self.Icon.Image="rbxassetid://"..tostring(value):gsub("rbxassetid://",""); return self end
 for _,column in pairs(columns) do connect(column.UIListLayout:GetPropertyChangedSignal("AbsoluteContentSize"),layoutResponsive) end
 function tab:Select() selectTab(index,false) end
 connect(icon.Activated,function() tab:Select() end)
 originals[icon]={BackgroundTransparency=1,ImageTransparency=index==1 and 0 or 0.6}
 originals[page]={BackgroundTransparency=1}
 tabHandles[index]=tab
 if index==1 then selectTab(1,true) else icon.ImageTransparency=0.6 end
 return tab
end
local objects=frame:GetDescendants()
table.insert(objects,frame)
for _,obj in ipairs(objects) do
 local p={}
 if obj:IsA("GuiObject") then p.BackgroundTransparency=obj.BackgroundTransparency end
 if obj:IsA("TextLabel") or obj:IsA("TextButton") or obj:IsA("TextBox") then p.TextTransparency=obj.TextTransparency; p.TextStrokeTransparency=obj.TextStrokeTransparency end
 if obj:IsA("ImageLabel") or obj:IsA("ImageButton") then p.ImageTransparency=obj.ImageTransparency end
 if obj.ClassName=="UIShadow" then p.Transparency=obj.Transparency end
 if next(p) then originals[obj]=p end
end
local state="open"
local version=0
local tabRevealVersion = 0
local tabRevealTweens = {}
for i,icon in ipairs(tabIcons) do tabPositions[i] = icon.Position end
local function revealTabs()
 tabRevealVersion = tabRevealVersion + 1
 local id = tabRevealVersion
 for _,t in ipairs(tabRevealTweens) do t:Cancel() end
 tabRevealTweens = {}
 for i,icon in ipairs(tabIcons) do
  icon.ImageTransparency = 1
  local p = tabPositions[i]
  icon.Position = UDim2.new(p.X.Scale,p.X.Offset - 6,p.Y.Scale,p.Y.Offset)
  task.delay((i - 1) * 0.045, function()
   if not alive or id ~= tabRevealVersion then return end
   local t = TS:Create(icon,TweenInfo.new(0.22,Enum.EasingStyle.Sine,Enum.EasingDirection.Out),{
    Position = tabPositions[i], ImageTransparency = i == selectedTab and 0 or 0.6
   })
   table.insert(tabRevealTweens,t)
   t:Play()
  end)
 end
end
onCleanup(function()
 tabRevealVersion = tabRevealVersion + 1
 for _,t in ipairs(tabRevealTweens) do t:Cancel() end
end)
local function animate(open,complete)
 version=version+1
 local id=version
 for _,t in ipairs(tweens) do t:Cancel() end
 tweens={}
 local info=TweenInfo.new(open and 0.28 or 0.2,Enum.EasingStyle.Sine,open and Enum.EasingDirection.Out or Enum.EasingDirection.In)
 for obj,properties in pairs(originals) do
 local goal={}
 for p,v in pairs(properties) do
  if not (open and obj:IsA("ImageButton") and p=="ImageTransparency") then goal[p]=open and v or 1 end
 end
 local t=TS:Create(obj,info,goal)
 table.insert(tweens,t)
 t:Play()
 end
 local t=TS:Create(scale,info,{Scale=open and 1 or 0.96})
 table.insert(tweens,t)
 if complete then
 local c
 c=connect(t.Completed,function(status)
 c:Disconnect()
 if alive and id==version and status==Enum.PlaybackState.Completed then complete() end
 end)
 end
 t:Play()
 if open then revealTabs() else
  tabRevealVersion = tabRevealVersion + 1
  for _,revealTween in ipairs(tabRevealTweens) do revealTween:Cancel() end
 end
end
connect(frame.Minimize.Activated,function()
 if state~="open" then return end
 state="minimizing"
 dragging=false
 animate(false,function() state="minimized"; frame.Visible=false; bar.Visible=true end)
end)
connect(bar.Activated,function()
 if state~="minimized" then return end
 state="open"
 bar.Visible=false
 frame.Visible=true
 animate(true)
end)
connect(frame.Close.Activated,function()
 if state=="closed" then return end
 state="closed"
 dragging=false
 bar.Visible=false
 animate(false,function() gui.Enabled=false end)
end)
connect(frame.Green.Activated,function()
 if state~="open" then return end
 state="restarting"; dragging=false
 animate(false,function()
  if not alive then return end
  frame.Visible=true
  selectTab(selectedTab,true)
  state="open"
  animate(true)
 end)
end)
onCleanup(function()
 for _,t in pairs(tabTweens) do t:Cancel() end
end)
connect(bar.MouseEnter,function() bar.BackgroundTransparency=0.5 end)
connect(bar.MouseLeave,function() bar.BackgroundTransparency=0.8 end)
connect(gui.Destroying,function()
 alive=false
 for _,cleanup in ipairs(cleanups) do pcall(cleanup) end
 version=version+1
 for _,t in ipairs(tweens) do t:Cancel() end
 for _,c in ipairs(connections) do c:Disconnect() end
end)
if UIS.TouchEnabled then
 for buttonIndex,button in ipairs(controls) do
  local target=Instance.new("TextButton")
  target.Name=button.Name.."TouchTarget"; target.Text=""; target.BackgroundTransparency=1; target.Size=UDim2.fromOffset(44,44)
  target.AnchorPoint=Vector2.new(.5,.5); target.Position=UDim2.new(1,-(30+(3-buttonIndex)*46),0,26); target.ZIndex=20; target.Parent=frame
  button.Position=UDim2.new(target.Position.X.Scale,target.Position.X.Offset-6.5,0,19)
  connect(target.Activated,function()
   if button.Name=="Close" then windowActions.Close() elseif button.Name=="Minimize" then windowActions.Minimize() else windowActions.Restart() end
  end)
 end
 bar.Size=UDim2.fromOffset(28,176)
end
local window={Gui=gui,Frame=frame,Tabs=tabHandles,Options=windowOptions}
function window:AddTab(config)
 local tab=addTab(config)
 task.defer(function() if alive and state=="open" then revealTabs() end end)
 return tab
end
function window:SelectTab(index) selectTab(index,false) end
function window:Minimize()
 if not alive or state~="open" then return end
 state="minimizing"; dragging=false
 animate(false,function() state="minimized"; frame.Visible=false; bar.Visible=true end)
end
function window:Open()
 if not alive then return end
 gui.Enabled=true
 state="open"; frame.Visible=true; bar.Visible=false; animate(true)
end
function window:Close()
 if not alive then return end
 state="closed"; dragging=false; bar.Visible=false
 animate(false,function() gui.Enabled=false end)
end
function window:Restart()
 if not alive or state~="open" then return end
 state="restarting"; dragging=false
 animate(false,function() state="open"; animate(true) end)
end
function window:GetState() return state end
function window:GetComponent(id) return windowOptions[id] end
function window:SetSize(value) preferredSize=value; layoutResponsive(); return self end
function window:SetViewportSize(value) viewportOverride=value; layoutResponsive(); return self end
function window:Destroy() if alive then for _,control in ipairs(componentHandles) do control:Destroy() end; gui:Destroy() end end
windowActions.Close=function() window:Close() end
windowActions.Minimize=function() window:Minimize() end
windowActions.Restart=function() window:Restart() end
layoutResponsive()
frame.Visible=true
bar.Visible=false
scale.Scale=0.96
for obj,properties in pairs(originals) do for p in pairs(properties) do obj[p]=1 end end
animate(true)
return window
end
return Library

    end)()
    assert(type(Zeen)=="table" and type(Zeen.CreateWindow)=="function", "Zeen UI library failed to initialize")
    local UI={}
    local function clone(v) return type(v)=="table" and table.clone(v) or v end
    local function equal(a,b)
        if type(a)~="table" or type(b)~="table" then return a==b end
        if #a~=#b then return false end
        for i,v in ipairs(a) do if b[i]~=v then return false end end
        return true
    end
    local function rows(options)
        local result,used={},{}
        for _,option in ipairs(options or {}) do
            local value=type(option)=="table" and (option.Value or option.Title) or option
            local title=tostring(type(option)=="table" and (option.Title or value) or value)
            if value~=nil then
                local label=title; local n=1
                while used[label] do n+=1; label=title.." ["..n.."]" end
                used[label]=true; result[#result+1]={value=value,label=label}
            end
        end
        return result
    end
    function UI:CreateWindow(settings)
        local native=Zeen:CreateWindow({Title=settings.Title,SubTitle=settings.Description or "Anime Breaker",Size=settings.Size or UDim2.fromOffset(681,430)})
        local gui=native.Gui or native.ScreenGui or Zeen.ScreenGui
        assert(gui,"Zeen UI did not expose a ScreenGui")
        local window={Gui=gui,Native=native,IsZeen=true,tabs={},controls={},ready=false,extraRoots={}}
        local Http=game:GetService("HttpService")
        local savePath="Foccus/anime-breaker-rayfield.json"
        function window:Notify(info)
            local text=tostring(info.Description or info.Content or "")
            pcall(function()
                game:GetService("StarterGui"):SetCore("SendNotification",{Title=tostring(info.Title or "Zeen Hub"),Text=text,Duration=info.Duration or 5})
            end)
        end
        function window:Save()
            if
                not self.ready
                or self.restoring
                or not settings.AutoSave
                or type(writefile) ~= "function"
            then
                return
            end
            self.saveVersion = (self.saveVersion or 0) + 1
            self.saveDue = os.clock() + 0.75
            if self.savePending then
                return
            end
            self.savePending = true
            task.spawn(function()
                repeat
                    task.wait(0.25)
                until not self.Gui.Parent or os.clock() >= self.saveDue
                self.savePending = false
                (setthreadidentity or setidentity)(8)
                if not self.Gui.Parent or not settings.AutoSave then
                    return
                end
                local data = {}
                for _, c in ipairs(self.controls) do
                    if c.flag and c.Instance.Parent then
                        data[c.flag] = c:Get()
                    end
                end
                local ok, err = pcall(function()
                    if isfolder and makefolder and not isfolder("Foccus") then
                        makefolder("Foccus")
                    end
                    writefile(savePath, Http:JSONEncode(data))
                end)
                if not ok then
                    warn("Zeen save: " .. tostring(err))
                end
            end)
        end
        function window:FinishSetup()
            self.restoring = true
            if true and readfile and isfile and isfile(savePath) then
                local ok, data = pcall(function()
                    return Http:JSONDecode(readfile(savePath))
                end)
                if ok and type(data) == "table" then
                    if self.migrateConfig then
                        self.migrateConfig(data)
                    end
                    for _, toggles in ipairs({ false, true }) do
                        for _, c in ipairs(self.controls) do
                            if (c.kind == "Toggle") == toggles and c.flag and data[c.flag] ~= nil then
                                local success, err = pcall(c.Set, c, data[c.flag])
                                if not success then
                                    warn("Zeen restore " .. c.flag .. ": " .. tostring(err))
                                end
                            end
                        end
                    end
                end
            end
            self.restoring = false
            self.ready = true
            local teleported = getgenv().ZeenTeleportSettings
            if type(teleported) == "table" then
                self.restoring = true
                for _, toggles in ipairs({ false, true }) do
                    for _, control in ipairs(self.controls) do
                        if
                            (control.kind == "Toggle") == toggles
                            and control.flag
                            and teleported[control.flag] ~= nil
                        then
                            local ok, err = pcall(control.Set, control, teleported[control.flag])
                            if not ok then
                                warn("Zeen teleport restore: " .. tostring(err))
                            end
                        end
                    end
                end
                getgenv().ZeenTeleportSettings = nil
                self.restoring = false
            end
        end
        function window:SectionTab() end
        function window:SelectTab(target)
            if target and type(target.Select)=="function" then pcall(function() target:Select() end) end
        end
        function window:Toggle()
            if gui.Enabled and native:GetState()=="open" then
                gui.Enabled=false
            else
                gui.Enabled=true
                if native:GetState()~="open" then native:Open() end
            end
        end
        function window:AddTab(tabSettings)
            local nativeTab=native:AddTab({Title=tabSettings.Title,Icon=tabSettings.Icon})
            local gameIcons = {
                Farming="75345030919501", ["Game Modes"]="90960801598341",
                ["Farm Raid"]="84717502643616", ["Farm Portal"]="94718413647563",
                ["Farm Trial"]="135376025449065", ["Magic Tower"]="140078747855046",
                Defense="111420325380645", ["Marine Invasion"]="97069439596127",
                Expedition="105540151516867", Halloween="82397514381992",
                Gacha="78403703728948", Automation="129105735584218",
                Weather="88018276828069", Webhook="85922626050675",
                Language="88093629785218", Config="136217738095209",
            }
            local icon = nativeTab.Icon
            if icon then
                icon.Image = "rbxassetid://" .. (gameIcons[tabSettings.Title] or gameIcons.Config)
                icon.ImageColor3 = Color3.new(1,1,1)
                icon.ScaleType = Enum.ScaleType.Fit
            end
            local group={pages={},title=tabSettings.Title,native=nativeTab}
            self.tabs[#self.tabs+1]=group
            function group:AddPage()
                local page={native=self.native,order=0}
                self.pages[#self.pages+1]=page
                for _,column in ipairs({self.native.Left,self.native.Right}) do
                    local layout=column and column:FindFirstChildOfClass("UIListLayout")
                    if layout then layout.Padding=UDim.new(0,4) end
                    local padding=column and column:FindFirstChildOfClass("UIPadding")
                    if padding then
                        padding.PaddingTop=UDim.new(0,3)
                        padding.PaddingBottom=UDim.new(0,4)
                    end
                end
                function page:nextSide(requested)
                    if requested=="Left" or requested=="Right" then return requested end
                    self.order+=1
                    return self.order%2==1 and "Left" or "Right"
                end
                local function uiDescription(value)
                    value=tostring(value or "")
                    return #value<=34 and value or ""
                end
                local function controlInstance(control)
                    local candidate=control and (control.Instance or control.Gui or control.Frame)
                    return candidate and typeof(candidate)=="Instance" and candidate or nil
                end
                local function register(kind,cfg,default)
                    local control={kind=kind,flag=cfg.Flag,value=clone(default),multi=cfg.Multi==true,muted=false}
                    function control:Get() return clone(self.value) end
                    function control:emit(silent) if not silent and cfg.Callback then cfg.Callback(self:Get()) end; if not silent then window:Save() end end
                    function control:receive(value)
                        if self.muted or equal(self.value,value) then return end
                        self.value=clone(value); self:emit(false)
                    end
                    window.controls[#window.controls+1]=control
                    return control
                end
                local function callSet(control,method,...)
                    if control.native and type(control.native[method])=="function" then return pcall(control.native[method],control.native,...) end
                    return false
                end
                function page:AddSection(value)
                    local title=type(value)=="table" and value.Title or value
                    if type(self.native.AddSection)=="function" then local ok,result=pcall(self.native.AddSection,self.native,{Title=title}); if ok then return result end end
                    return self:AddParagraph({Title=title,Description=""})
                end
                function page:AddParagraph(cfg)
                    local control=self.native:AddButton({
                        Title=cfg.Title, Description=cfg.Description or cfg.Content or "",
                        Side=self:nextSide(cfg.Side or (cfg.Column==2 and "Right" or "Left")),
                        Callback=function() end, Enabled=false,
                    })
                    local frame=control.Instance
                    local label=frame and frame:FindFirstChild("Description")
                    if label then
                        label.TextWrapped=true
                        label.TextTruncate=Enum.TextTruncate.None
                        label.AutomaticSize=Enum.AutomaticSize.Y
                        label.Size=UDim2.new(1,-24,0,0)
                        local function fit()
                            if frame.Parent then frame.Size=UDim2.new(1,0,0,math.max(60,38+label.AbsoluteSize.Y)) end
                        end
                        label:GetPropertyChangedSignal("AbsoluteSize"):Connect(fit)
                        fit()
                    end
                    function control:Set(value)
                        if value.Title then self:SetTitle(value.Title) end
                        self:SetDescription(value.Description or value.Content or "")
                    end
                    return control
                end
                function page:AddButton(cfg)
                    local control=self.native:AddButton(cfg.Title,{Title=cfg.Title,Description=uiDescription(cfg.Description),Side=self:nextSide(cfg.Side or (cfg.Column==2 and "Right" or cfg.Column==1 and "Left" or nil)),Callback=cfg.Callback})
                    return control
                end
                function page:AddToggle(cfg)
                    local c=register("Toggle",cfg,cfg.Default==true)
                    c.native=self.native:AddToggle(cfg.Title,{Title=cfg.Title,Description=uiDescription(cfg.Description),Side=self:nextSide(cfg.Side or (cfg.Column==2 and "Right" or cfg.Column==1 and "Left" or nil)),Default=c.value,Callback=function(v) c:receive(v==true) end})
                    c.Instance=controlInstance(c.native)
                    function c:Set(value,silent) self.value=value==true; self.muted=true; callSet(self,"SetValue",self.value,true); self.muted=false; self:emit(silent) end
                    return c
                end
                function page:AddInput(cfg)
                    local c=register("Input",cfg,tostring(cfg.Default or ""))
                    c.native=self.native:AddInput(cfg.Title,{Title=cfg.Title,Description=uiDescription(cfg.Description),Side=self:nextSide(cfg.Side or (cfg.Column==2 and "Right" or cfg.Column==1 and "Left" or nil)),Default=c.value,Placeholder=cfg.Placeholder,Finished=cfg.Finished,MaxLength=cfg.MaxLength,Callback=function(v) c:receive(tostring(v or "")) end})
                    c.Instance=controlInstance(c.native)
                    function c:Set(value,silent) self.value=tostring(value or ""); self.muted=true; callSet(self,"SetValue",self.value,true); self.muted=false; self:emit(silent) end
                    return c
                end
                function page:AddSlider(cfg)
                    local limits=cfg.Range or {cfg.Min or 0,cfg.Max or 100}
                    local c=register("Slider",cfg,cfg.Default or limits[1])
                    c.native=self.native:AddSlider(cfg.Title,{Title=cfg.Title,Description=uiDescription(cfg.Description),Side=self:nextSide(cfg.Side or (cfg.Column==2 and "Right" or cfg.Column==1 and "Left" or nil)),Min=limits[1],Max=limits[2],Default=c.value,Rounding=cfg.Rounding or 0,Callback=function(v) c:receive(tonumber(v) or 0) end})
                    c.Instance=controlInstance(c.native)
                    function c:Set(value,silent) self.value=tonumber(value) or 0; self.muted=true; callSet(self,"SetValue",self.value,true); self.muted=false; self:emit(silent) end
                    return c
                end
                function page:AddDropdown(cfg)
                    local c=register("Dropdown",cfg,nil); c.rows=rows(cfg.Options); c.value=cfg.Multi and {} or nil
                    local function labels() local result={}; for _,row in ipairs(c.rows) do result[#result+1]=row.label end; return result end
                    local function has(value,needle)
                        if type(value)~="table" then return false end
                        if value[needle]==true then return true end
                        return table.find(value,needle)~=nil
                    end
                    local function encode(value)
                        if not c.multi then for _,row in ipairs(c.rows) do if row.value==value then return row.label end end; return value end
                        local result={}; for _,row in ipairs(c.rows) do if has(value,row.value) then result[#result+1]=row.label end end; return result
                    end
                    local function decode(value)
                        local function one(label) for _,row in ipairs(c.rows) do if row.label==label then return row.value end end; return label end
                        if not c.multi then return one(value) end
                        local result={}
                        if type(value)=="table" then
                            for key,selected in pairs(value) do
                                local label=selected==true and key or (type(selected)=="string" and selected or nil)
                                if label~=nil then result[#result+1]=one(label) end
                            end
                        end
                        return result
                    end
                    c.value=cfg.Multi and decode(cfg.Default or {}) or cfg.Default
                    local zeenConfig={Title=cfg.Title,Description=uiDescription(cfg.Description),Side=self:nextSide(cfg.Side or (cfg.Column==2 and "Right" or cfg.Column==1 and "Left" or nil)),Values=labels(),Default=encode(c.value),Multi=c.multi,AutoReload=cfg.AutoReload,RefreshInterval=cfg.RefreshInterval,OptionsProvider=function() return labels() end,Callback=function(v) c:receive(decode(v)) end}
                    c.native=self.native:AddDropdown(cfg.Title,zeenConfig); c.Instance=controlInstance(c.native)
                    function c:Set(value,silent) self.value=self.multi and decode(value or {}) or value; self.muted=true; callSet(self,"SetValue",encode(self.value),true); self.muted=false; self:emit(silent) end
                    function c:Reload(options) self.rows=rows(options); if self.native and type(self.native.Refresh)=="function" then pcall(self.native.Refresh,self.native); callSet(self,"SetValue",encode(self.value),true) end end
                    function c:SetOpen(open) if self.native then pcall(function() if open and self.native.Open then self.native:Open() elseif not open and self.native.Close then self.native:Close() end end) end end
                    return c
                end
                return page
            end
            return group
        end
        gui.Destroying:Connect(function() if type(native.Destroy)=="function" then pcall(native.Destroy,native) end end)
        return window
    end
    return UI
end


local WeatherAlerts = (function()
    local WeatherAlerts = {}

    function WeatherAlerts.normalizeUser(value)
        local text = tostring(value or ""):match("^%s*(.-)%s*$")
        text = text:match("^<@!?(%d+)>$") or text
        if text == "" then
            return ""
        end
        if #text >= 17 and #text <= 20 and text:match("^%d+$") then
            return text
        end
        return nil
    end

    function WeatherAlerts.events(active, seen, now, baseline)
        local result = {}
        for key, expires in pairs(seen) do
            if now > expires + 3600 then
                seen[key] = nil
            end
        end
        for _, weather in ipairs(active) do
            local window = weather.Window or {}
            local started, ends = tonumber(window.OpensAt), tonumber(window.ClosesAt)
            if type(weather.Id) == "string" and started and ends and ends > now then
                local key = weather.Id .. ":" .. tostring(started)
                if not seen[key] then
                    seen[key] = ends
                    if not baseline then
                        result[#result + 1] =
                            { id = weather.Id, start = started, ends = ends, forced = window.Forced == true }
                    end
                end
            end
        end
        return result
    end

    function WeatherAlerts.payload(event, name, userId, selected)
        local validUser = WeatherAlerts.normalizeUser(userId)
        local ping = validUser and validUser ~= "" and selected[event.id] == true
        return {
            username = "Zeen",
            content = ping and ("<@" .. validUser .. ">") or "",
            allowed_mentions = { parse = {}, users = ping and { validUser } or {} },
            embeds = {
                {
                    title = "Zeen | Weather Started",
                    description = "**" .. tostring(name or event.id) .. "** has started!",
                    color = 10181046,
                    fields = {
                        { name = "Weather", value = tostring(name or event.id), inline = true },
                        {
                            name = "Started",
                            value = "<t:" .. math.floor(event.start) .. ":F>",
                            inline = true,
                        },
                        { name = "Ends", value = "<t:" .. math.floor(event.ends) .. ":R>", inline = true },
                    },
                    footer = { text = "Anime Breaker | Zeen" },
                },
            },
        }
    end

    return WeatherAlerts
end)()

local WeatherBoosts = (function()
    local WeatherBoosts = {}
    WeatherBoosts.__index = WeatherBoosts

    function WeatherBoosts.new()
        return setmetatable(
            { enabled = false, weathers = {}, boosts = {}, managed = {}, retry = {}, nextAction = 0 },
            WeatherBoosts
        )
    end

    function WeatherBoosts:owns(id)
        return self.managed[id] == true or (self.enabled and table.find(self.boosts, id) ~= nil)
    end

    function WeatherBoosts:step(active, data, now, fire)
        local matches = false
        local selected = {}
        if self.enabled then
            for _, id in ipairs(self.boosts) do
                selected[id] = true
                self.managed[id] = true
            end
            for _, weather in ipairs(active) do
                if table.find(self.weathers, weather.Id) then
                    matches = true
                    break
                end
            end
        end
        self.active = matches
        if now < self.nextAction then
            return
        end
        local ids = {}
        for id in pairs(self.managed) do
            ids[#ids + 1] = id
        end
        table.sort(ids)
        local durations, paused = data.Consumables or {}, data.ConsumablePaused or {}
        for _, wantActive in ipairs({ false, true }) do
            for _, id in ipairs(ids) do
                local wanted = matches and selected[id] == true
                local remaining = tonumber(durations[id]) or 0
                local isPaused = paused[id] == true
                if not selected[id] and (remaining <= 0 or isPaused) then
                    self.managed[id] = nil
                    self.retry[id] = nil
                elseif wanted == wantActive and now >= (self.retry[id] or 0) then
                    if remaining > 0 and isPaused == wanted then
                        fire("ConsumableSystem", "Pause", id)
                        self.lastAction = { item = id, action = wanted and "resume" or "pause" }
                        self.retry[id] = now + 3
                        self.nextAction = now + 0.4
                        return
                    elseif wanted and remaining <= 0 and (tonumber((data.Items or {})[id]) or 0) > 0 then
                        fire("ItemSystem", "Use", id, nil, nil)
                        self.lastAction = { item = id, action = "use" }
                        self.retry[id] = now + 3
                        self.nextAction = now + 0.4
                        return
                    end
                end
            end
        end
    end

    return WeatherBoosts
end)()
local EventAlerts = (function()
    local EventAlerts = {}
    function EventAlerts.url(value)
        local url = tostring(value or ""):match("^%s*(.-)%s*$")
        if url == "" then
            return ""
        end
        local host, id, token = url:match("^https://([^/]+)/api/webhooks/(%d+)/([%w_%-]+)$")
        if
            (
                host == "discord.com"
                or host == "discordapp.com"
                or host == "canary.discord.com"
                or host == "ptb.discord.com"
            )
            and id
            and token
        then
            return url
        end
        return nil
    end
    function EventAlerts.snapshot(data, systems, catalogs)
        local result = { counts = {}, labels = {}, heroes = {} }
        for kind, system in pairs(systems) do
            local list = system.List
            local catalog = catalogs[kind] or {}
            if list and type(data[list]) == "table" then
                for uid, entry in pairs(data[list]) do
                    local id, count
                    if kind == "Item" and type(entry) == "number" then
                        id = uid
                        count = entry
                    elseif type(entry) == "table" and type(entry.Id) == "string" then
                        id = entry.Id
                        count = 1
                    end
                    if id and count and count > 0 then
                        local key = kind .. ":" .. id
                        local info = catalog[id]
                        result.counts[key] = (result.counts[key] or 0) + count
                        result.labels[key] = (system.Name or kind)
                            .. " — "
                            .. tostring(info and info.Name or id)
                        if kind == "Pet" and info and info.Rarity == "Broken" then
                            result.heroes[tostring(uid)] = { id = id, name = info.Name or id }
                        end
                    end
                end
            end
        end
        return result
    end
    function EventAlerts.diff(previous, current, pending)
        local broken = {}
        if not previous then
            return broken
        end
        for key, count in pairs(current.counts) do
            local gain = count - (previous.counts[key] or 0)
            if gain > 0 then
                local entry = pending[key] or { name = current.labels[key], amount = 0 }
                entry.amount += gain
                pending[key] = entry
            end
        end
        for uid, hero in pairs(current.heroes) do
            if not previous.heroes[uid] then
                broken[hero.name] = (broken[hero.name] or 0) + 1
            end
        end
        return broken
    end
    function EventAlerts.lines(pending)
        local keys = {}
        for key in pairs(pending) do
            keys[#keys + 1] = key
        end
        table.sort(keys)
        local lines, total = {}, 0
        for i, key in ipairs(keys) do
            local entry = pending[key]
            local line = "+" .. tostring(entry.amount) .. " " .. entry.name
            if total + #line > 3300 then
                lines[#lines + 1] = "… " .. tostring(#keys - i + 1) .. " additional item types."
                break
            end
            lines[#lines + 1] = line
            total += #line + 1
        end
        return #lines > 0 and table.concat(lines, "\n")
            or "No new inventory items detected in the last 30 seconds."
    end
    function EventAlerts.payload(kind, description, userId, ping, playerName, timestamp)
        local titles = {
            Broken = "Broken Hero Obtained",
            Disconnected = "Disconnected from Roblox",
            Inventory = "Inventory Update — 30 seconds",
        }
        local mention = ping
            and type(userId) == "string"
            and userId:match("^%d+$")
            and #userId >= 17
            and #userId <= 20
        return {
            username = "Zeen",
            content = mention and "<@" .. userId .. ">" or "",
            allowed_mentions = { parse = {}, users = mention and { userId } or {} },
            embeds = {
                {
                    title = "Zeen | " .. (titles[kind] or kind),
                    description = description,
                    color = kind == "Broken" and 16766720 or kind == "Disconnected" and 15158332 or 5793266,
                    footer = { text = "Zeen | " .. playerName },
                    timestamp = os.date("!%Y-%m-%dT%H:%M:%SZ", timestamp),
                },
            },
        }
    end
    return EventAlerts
end)()

local Runtime = {}
Runtime.__index = Runtime

function Runtime:stop()
    if self.setIdentity then
        self.setIdentity(8)
    end
    self.state.running = false
    self.state.enabled = false
    if self.state.antiAFKStop then
        self.state.antiAFKStop()
    end
    if self.window.Gui.Parent then
        self.window.Gui:Destroy()
    end
end

function Runtime.new()
    local G = getgenv()
    local previous = G.FoccusAnimeBreaker
    if previous then
        if previous.runtime and previous.runtime.stop then
            previous.runtime:stop()
        end
        previous.running = false
        previous.enabled = false
        if previous.antiAFKConnection then
            previous.antiAFKConnection:Disconnect()
        end
        if previous.window and previous.window.Gui then
            previous.window.Gui:Destroy()
        end
    end

    local setIdentity = setthreadidentity or setidentity
    assert(setIdentity, "Executor does not support thread identity")
    setIdentity(2)
    local Players = game:GetService("Players")
    local CollectionService = game:GetService("CollectionService")
    local player = Players.LocalPlayer
    local Library = require(game.ReplicatedStorage.Framework.Library)
    local maps = Library:GetData("MapData")
    local enemies = Library:GetData("EnemyData")
    local raids = Library:GetData("GamemodeData").Raid
    local GamemodeService = Library:GetService("GamemodeService")
    local WeatherService = Library:GetService("WeatherService")
    local MultiplierService = Library:GetService("MultiplierService")
    local GuiService = Library:GetService("GuiService")
    local AutoService = Library:GetService("AutoService")
    local DailyRewardService = Library:GetService("DailyRewardService")
    local chestData = Library:GetData("ChestData")
    local dailyData = Library:GetData("DailyRewardData")
    local timeData = Library:GetData("TimeRewardData")
    local battlepassData = Library:GetData("BattlepassData")
    local weatherData = Library:GetData("WeatherData")
    local boostData = Library:GetData("BoostData")
    local consumableData = Library:GetData("ItemData.Consumable")
    local spawnBossData = Library:GetData("SpawnBossData")
    local globalBossData = Library:GetData("GlobalBossData")
    setIdentity(8)
    local UI = createZeenUI()
    local window = UI:CreateWindow({
        Title = "Zeen",
        Description = "Anime Breaker",
        Icon = "rbxassetid://113695702338739",
        Size = UDim2.fromOffset(680, 430),
        Loading = true,
        LoadingDuration = 2,
        AutoSave = true,
        ConfigFolder = "Foccus",
        ConfigName = "anime-breaker-mainv2.json",
    })
    local state = {
        running = true,
        enabled = false,
        selected = {},
        world = nil,
        target = nil,
        attacks = 0,
        defeated = 0,
        status = "Disabled",
        window = window,
    }
    G.FoccusAnimeBreaker = state
    state.trialPriorityVersion = 1
    state.fastGamemodeVersion = 1
    local self = setmetatable({
        setIdentity = setIdentity,
        Players = Players,
        CollectionService = CollectionService,
        player = player,
        Library = Library,
        maps = maps,
        enemies = enemies,
        raids = raids,
        GamemodeService = GamemodeService,
        WeatherService = WeatherService,
        MultiplierService = MultiplierService,
        GuiService = GuiService,
        AutoService = AutoService,
        DailyRewardService = DailyRewardService,
        chestData = chestData,
        dailyData = dailyData,
        timeData = timeData,
        battlepassData = battlepassData,
        weatherData = weatherData,
        boostData = boostData,
        consumableData = consumableData,
        spawnBossData = spawnBossData,
        globalBossData = globalBossData,
        window = window,
        state = state,
    }, Runtime)
    state.runtime = self
    local ok, err = pcall(function()
        state.initStage = "buildTabs"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildTabs()
        state.initStage = "buildFarmUI"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildFarmUI()
        state.initStage = "buildGhoulFarm"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildGhoulFarm()
        state.initStage = "buildFarmModeUI"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildFarmModeUI()
        state.initStage = "buildAutoCollectFragments"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildAutoCollectFragments()
        state.initStage = "buildAutoCollectHogyoku"
        self:buildAutoCollectHogyoku()
        state.initStage = "buildModes"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildModes()
        state.initStage = "buildTrialShop"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildTrialShop()
        state.initStage = "buildUtilities"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildUtilities()
        state.initStage = "buildWeatherEquip"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildWeatherEquip()
        state.initStage = "buildWeatherBoosts"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildWeatherBoosts()
        state.initStage = "buildWeatherWebhook"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildWeatherWebhook()
        state.initStage = "buildGacha"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildGacha()
        state.initStage = "buildHalloween"
        task.wait()
        self.setIdentity(8)
        self:buildHalloween()
        state.initStage = "buildReconnect"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildReconnect()
        self.state.extraConfigKeys = {
            "raidWaitTickets",
            "raidTicketAmount",
            "autoFarmWorldBoss",
            "autoFarmGhouls",
            "uiLanguage",
            "eventWebhookUrl",
            "eventWebhookEvents",
            "eventWebhookUser",
            "eventWebhookPings",
            "autoExecuteUrl",
            "autoExecute",
            "invasionPriority",
            "invasionShopItems",
            "invasionShopBuy",
            "invasionEnter",
            "invasionFarm",
            "invasionLeave",
            "invasionWave",
            "invasionWait",
            "invasionPlayers",
            "invasionEquip",
            "invasionBoost",
            "currencyBoxes",
            "currencyBoxAuto",
            "fruitBoxAuto",
        }
        state.initStage = "buildAutoExecute"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildAutoExecute()
        state.initStage = "buildMarineInvasion"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildMarineInvasion()
        state.initStage = "buildMagicTower"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildMagicTower()
        state.initStage = "buildDefense"
        task.wait()
        self.setIdentity(8)
        self:buildDefense()
        state.initStage = "buildInvasionShop"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildInvasionShop()
        state.initStage = "buildExpedition"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildExpedition()
        state.initStage = "buildModeShortcuts"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildModeShortcuts()
        state.initStage = "buildEventWebhook"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildEventWebhook()
        state.initStage = "buildLanguage"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildLanguage()
        state.initStage = "buildConfig"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildConfig()
        self.tabs.automation:RouteSection("Visual")
        self:hideRewards()
        self:hideTeleport()
        self:repairInput()
        self:bindShortcut()
        state.initStage = "buildMobileButton"
        print("[Zeen] Initializing: " .. state.initStage)
        task.wait()
        self.setIdentity(8)
        self:buildMobileButton()
        self.setIdentity(8)
        state.initStage = "Restore settings"
        self.window:FinishSetup()
        self.setIdentity(8)
        state.initStage = "Attach language"
        TBLanguage:attach(self.window.Gui, self.window.extraRoots)
        state.initStage = "Start farm"
        self:startFarm()
        state.initStage = "Ready"
        task.defer(function()
            if state.running and self.window.Gui.Parent then
                self.setIdentity(8)
                self.window:SelectTab(self.tabs.farming.NativeTab)
            end
        end)
    end)
    if not ok then
        state.initError = (state.initStage or "Build interface") .. ": " .. tostring(err)
        self:stop()
        error("Zeen initialization failed: " .. state.initError, 0)
    end
    return self
end

function Runtime:restoreWorldBossAutos()
    local boss = self.state.worldBoss
    if not boss then
        return
    end
    local settings = self.Library.PlayerData.AutoSettings or {}
    for id in pairs(boss.pausedAuto) do
        if settings[id] ~= true then
            self.Library.Remote:Fire("AutoSystem", "Toggle", id)
        end
        boss.pausedAuto[id] = nil
    end
end

function Runtime:updateWorldBossPriority(now, cache)
    local s, L = self.state, self.Library
    local boss = s.worldBoss
    if not boss then
        return false
    end
    local function alive(enemy)
        return enemy
            and enemy.Parent
            and enemy:IsA("BasePart")
            and enemy:GetAttribute("Type") == "GlobalBoss"
            and enemy:GetAttribute("Id") == "Pumpkin Boss"
            and not enemy:GetAttribute("Dead")
            and (tonumber(enemy:GetAttribute("HP")) or 0) > 0
    end
    local function findLiveBoss()
        local enemies = workspace:FindFirstChild("_ENEMIES")
        local server = enemies and enemies:FindFirstChild("Server")
        local globalBosses = server and server:FindFirstChild("GlobalBoss")
        if not globalBosses then
            return nil
        end
        for _, enemy in ipairs(globalBosses:QueryDescendants("BasePart[$Id]")) do
            if alive(enemy) then
                return enemy
            end
        end
        return nil
    end
    local function release(reason)
        if boss.active then
            s.target = nil
            s.farmContext = nil
            s.rangeSpot = nil
            boss.lastResult = reason
        end
        boss.active = false
        boss.target = nil
        boss.missingSince = nil
        self:restoreWorldBossAutos()
    end
    if not boss.enabled then
        release("disabled")
        return false
    end
    if not alive(boss.target) then
        boss.target = nil
        for enemy in pairs(cache) do
            if alive(enemy) then
                boss.target = enemy
                break
            end
        end
        if not boss.target then
            boss.target = findLiveBoss()
        end
    end
    if boss.target then
        cache[boss.target] = true
    end
    if not boss.target then
        if boss.active then
            boss.missingSince = boss.missingSince or now
            if now - boss.missingSince < 3 then
                return true
            end
        end
        release("not spawned")
        return false
    end
    boss.missingSince = nil
    boss.active = true
    if now >= (boss.nextAuto or 0) then
        boss.nextAuto = now + 2
        local settings = L.PlayerData.AutoSettings or {}
        for id, enabled in pairs(settings) do
            if type(id) == "string" and id:sub(1, 4) == "Auto" and enabled == true and not boss.pausedAuto[id] then
                boss.pausedAuto[id] = true
                L.Remote:Fire("AutoSystem", "Toggle", id)
            end
        end
    end
    return true
end

function Runtime:resolveWorldBossFarm(mode, now)
    local s, L = self.state, self.Library
    local boss = s.worldBoss
    if not boss or not boss.active then
        return false
    end
    if mode and mode ~= "" then
        s.status = "Leaving " .. tostring(mode) .. " for Pumpkin Boss"
        if now >= boss.nextQuit then
            boss.nextQuit = now + 2
            L.Remote:Fire("GamemodeSystem", "Quit")
        end
        return true
    end
    if self.player:GetAttribute("Teleporting") then
        s.status = "Waiting for Pumpkin Boss world teleport"
        return true
    end
    local data = self.globalBossData["Pumpkin Boss"]
    local world = data and data.Map or "Halloween 2026 [Zone 1]"
    if L.PlayerData.CurrentMap ~= world then
        s.status = "Travelling to Pumpkin Boss"
        if now >= boss.nextTravel then
            boss.nextTravel = now + 3
            L.Remote:Fire("TeleportSystem", "To", world)
        end
        return true
    end
    if not boss.target or not boss.target.Parent then
        s.status = "Locating Pumpkin Boss"
        return true
    end
    if boss.target:GetAttribute("Shield") then
        s.status = "Waiting for Pumpkin Boss shield"
        return true
    end
    s.status = "World Boss priority: Pumpkin Boss"
    return true,
        {
            key = "world-boss:" .. boss.target.Name,
            world = world,
            selected = { ["Pumpkin Boss"] = true },
            secretTarget = boss.target,
            worldBoss = true,
        }
end

function Runtime:buildGhoulFarm()
    local s = self.state
    s.ghouls = { enabled = false, active = false, nextTravel = 0, nextQuit = 0, pausedAuto = {} }
    self.ghoulBosses = {}
    local data = self.spawnBossData
    for _, group in pairs(data) do
        for id, boss in pairs(group.Bosses or {}) do
            if boss.Map == "TokyoGhoul" then
                self.ghoulBosses[id] = boss
            end
        end
    end
    self.tabs.farming:AddSection("Ghouls")
    s.controls.autoFarmGhouls = self.tabs.farming:AddToggle({
        Title = "Auto Farm Ghouls",
        Description = "Highest priority: leave gamemodes, defeat the spawned Rogue Ghoul, then resume farming.",
        Default = false,
        Callback = function(value)
            s.ghouls.enabled = value
            if not value then
                s.ghouls.active = false
                s.ghouls.id = nil
                s.ghouls.target = nil
                s.target = nil
                s.farmContext = nil
            end
        end,
    })
    self.window.Gui.Destroying:Connect(function()
        task.spawn(function()
            self.setIdentity(2)
            self:restoreGhoulAutos()
        end)
    end)
end

function Runtime:restoreGhoulAutos()
    local g = self.state.ghouls
    if not g then
        return
    end
    local settings = self.Library.PlayerData.AutoSettings or {}
    for id in pairs(g.pausedAuto) do
        if settings[id] ~= true then
            self.Library.Remote:Fire("AutoSystem", "Toggle", id)
        end
        g.pausedAuto[id] = nil
    end
end

function Runtime:updateGhoulPriority(now, cache)
    local s, L = self.state, self.Library
    local g = s.ghouls
    if not g then
        return false
    end
    local function release(reason)
        if g.active then
            s.target = nil
            s.farmContext = nil
            s.rangeSpot = nil
            g.lastResult = reason
        end
        g.active = false
        g.id = nil
        g.target = nil
        g.missingSince = nil
        self:restoreGhoulAutos()
    end
    if not g.enabled then
        release("disabled")
        return false
    end
    if not L.PlayerData.UnlockedMap.TokyoGhoul then
        release("world locked")
        return false
    end
    local server = game.ReplicatedStorage:FindFirstChild("Server")
    local timers = server and server:FindFirstChild("SpawnBoss")
    local function announced(id)
        return timers and (tonumber(timers:GetAttribute(id)) or 0) > workspace:GetServerTimeNow()
    end
    local function live(e)
        return e
            and e.Parent
            and e:IsA("BasePart")
            and self.ghoulBosses[e:GetAttribute("Id")]
            and not e:GetAttribute("Dead")
            and (tonumber(e:GetAttribute("HP")) or 0) > 0
    end
    if
        g.target
        and g.target.Parent
        and (g.target:GetAttribute("Dead") or (tonumber(g.target:GetAttribute("HP")) or 1) <= 0)
    then
        g.completed = (g.completed or 0) + 1
        release("defeated")
        g.nextScan = now + 0.5
        return false
    end
    if now < (g.nextScan or 0) then
        return false
    end
    if not live(g.target) then
        g.target = nil
        for e in pairs(cache) do
            if live(e) and (not g.id or e:GetAttribute("Id") == g.id) then
                g.target = e
                g.id = e:GetAttribute("Id")
                break
            end
        end
    end
    if not g.id then
        local ids = {}
        for id in pairs(self.ghoulBosses) do
            if announced(id) then
                ids[#ids + 1] = id
            end
        end
        table.sort(ids)
        g.id = ids[1]
    end
    if not g.id then
        release("no spawn")
        return false
    end
    if not g.target and not announced(g.id) then
        g.missingSince = g.missingSince or now
        if now - g.missingSince >= 3 then
            release("spawn ended or removed")
            return false
        end
    else
        g.missingSince = nil
    end
    g.active = true
    if now >= (g.nextAuto or 0) then
        g.nextAuto = now + 2
        local settings = L.PlayerData.AutoSettings or {}
        for _, id in ipairs({
            "AutoRaid",
            "AutoPortal",
            "AutoTower",
            "AutoInvasion",
            "AutoTrial",
            "AutoTimeTrial",
        }) do
            if settings[id] == true then
                g.pausedAuto[id] = true
                L.Remote:Fire("AutoSystem", "Toggle", id)
            end
        end
    end
    return true
end

function Runtime:resolveGhoulFarm(mode, now)
    local s, L = self.state, self.Library
    local g = s.ghouls
    if not g or not g.active then
        return false
    end
    if mode and mode ~= "" then
        s.status = "Leaving " .. tostring(mode) .. " for " .. g.id
        if now >= g.nextQuit then
            g.nextQuit = now + 2
            L.Remote:Fire("GamemodeSystem", "Quit")
        end
        return true
    end
    if self.player:GetAttribute("Teleporting") then
        s.status = "Waiting for Ghoul City teleport"
        return true
    end
    if L.PlayerData.CurrentMap ~= "TokyoGhoul" then
        s.status = "Travelling to Ghoul City"
        if now >= g.nextTravel then
            g.nextTravel = now + 3
            L.Remote:Fire("TeleportSystem", "To", "TokyoGhoul")
        end
        return true
    end
    if not g.target or not g.target.Parent then
        s.status = "Locating " .. g.id
        return true
    end
    if g.target:GetAttribute("Shield") then
        s.status = "Waiting for ghoul shield"
        return true
    end
    return true,
        {
            key = "ghoul:" .. g.target.Name,
            world = "TokyoGhoul",
            selected = { [g.id] = true },
            secretTarget = g.target,
            ghoul = true,
        }
end

function Runtime:buildAutoCollectFragments()
    local source = [==[
local G = getgenv()
local old = G.FoccusFragmentCollector
if old then old.enabled = false end

local Players = game:GetService("Players")
local Collection = game:GetService("CollectionService")
local HttpService = game:GetService("HttpService")
local Teleport = game:GetService("TeleportService")
local player = Players.LocalPlayer
local setIdentity = setthreadidentity or setidentity
if setIdentity then setIdentity(2) end
local Library = require(game:GetService("ReplicatedStorage"):WaitForChild("Framework"):WaitForChild("Library"))
local SpawnItemService = Library:GetService("SpawnItemService")
local seen = {}
local saved = G.FoccusFragmentVisited
if type(saved) == "string" then
    local ok, ids = pcall(HttpService.JSONDecode, HttpService, saved)
    if ok and type(ids) == "table" then
        for _, id in ipairs(ids) do
            if type(id) == "string" then seen[id] = true end
        end
    end
end
G.FoccusFragmentVisited = nil
local C = {
    priorityVersion = 2,
    enabled = G.FoccusFragmentRestore == true,
    serverHop = G.FoccusFragmentHopRestore == true,
    seen = seen,
    target = nil,
    scanReady = false,
    nextHopAt = os.clock() + 3,
    nextPromptAt = 0,
    collected = 0,
    hops = 0,
}
G.FoccusFragmentRestore = nil
G.FoccusFragmentHopRestore = nil
G.FoccusFragmentCollector = C
seen[game.JobId] = true

local function count()
    local data = Library.PlayerData
    return tonumber(data and data.Items and data.Items.CommandmentFragment) or 0
end

local function point(item)
    if item:IsA("BasePart") then return item.Position end
    if item:IsA("Model") then return item:GetPivot().Position end
    local part = item:FindFirstChildWhichIsA("BasePart", true)
    return part and part.Position or nil
end

local function valid(item)
    if not item or not item.Parent or not Collection:HasTag(item, "SpawnItem") then return false end
    if item:GetAttribute("SpawnId") ~= "Commandments"
        or item:GetAttribute("Type") ~= "CommandmentFragment"
        or item:GetAttribute("OwnerId") ~= player.UserId then return false end
    if item:GetAttribute("Forced") == true then return true end
    local data = Library.PlayerData
    if not data then return false end
    local ok, visible = pcall(SpawnItemService.CanSee, player, data,
        "Commandments", "CommandmentFragment", item:GetAttribute("Seed"))
    return ok and visible == true
end

local function findNearest(root)
    local best, distance = nil, math.huge
    for _, item in ipairs(Collection:GetTagged("SpawnItem")) do
        if item ~= C.ignoreTarget and valid(item) then
            local p = point(item)
            if p then
                local d = (root.Position - p).Magnitude
                if d < distance then best, distance = item, d end
            end
        end
    end
    return best
end

local function requestServers(url)
    local requestFn = request or http_request or (syn and syn.request)
    if type(requestFn) == "function" then
        local response = requestFn({Url = url, Method = "GET"})
        if response and tonumber(response.StatusCode) == 200 then return response.Body end
        error("Server list HTTP " .. tostring(response and response.StatusCode))
    end
    if setIdentity then setIdentity(8) end
    local ok, body = pcall(function() return game:HttpGet(url) end)
    if setIdentity then setIdentity(2) end
    if not ok then error(body) end
    return body
end

local function nextServer()
    local cursor, available = nil, {}
    for _ = 1, 3 do
        local url = "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100&excludeFullGames=true"
        if cursor then url ..= "&cursor=" .. HttpService:UrlEncode(cursor) end
        local page = HttpService:JSONDecode(requestServers(url))
        for _, server in ipairs(page.data or {}) do
            if type(server.id) == "string" and server.id ~= game.JobId
                and tonumber(server.playing) and tonumber(server.maxPlayers)
                and server.playing < server.maxPlayers then
                available[#available + 1] = server
            end
        end
        if #available >= 20 or not page.nextPageCursor then break end
        cursor = page.nextPageCursor
    end
    if #available == 0 then return nil end
    local fresh = {}
    for _, server in ipairs(available) do
        if not seen[server.id] then fresh[#fresh + 1] = server end
    end
    if #fresh == 0 then
        table.clear(seen)
        seen[game.JobId] = true
        fresh = available
    end
    table.sort(fresh, function(a, b) return a.playing < b.playing end)
    return fresh[math.random(1, math.min(#fresh, 10))].id
end

local function hop()
    local queue = queue_on_teleport or queueonteleport or (syn and syn.queue_on_teleport)
    if type(queue) ~= "function" then error("Executor sem queue_on_teleport") end
    local destination = nextServer()
    if not destination then error("Nenhum servidor publico disponivel") end
    seen[destination] = true
    local ids = {}
    for id in pairs(seen) do ids[#ids + 1] = id end
    while #ids > 80 do table.remove(ids, 1) end
    local bootstrap = "local G=getgenv()\nG.FoccusFragmentRestore=true\nG.FoccusFragmentHopRestore=true\n"
        .. "G.FoccusFragmentVisited=" .. string.format("%q", HttpService:JSONEncode(ids)) .. "\n"
        .. "G.FoccusFragmentWorkerSource=" .. string.format("%q", G.FoccusFragmentWorkerSource) .. "\n"
        .. "assert(loadstring(G.FoccusFragmentWorkerSource))()"
    queue(bootstrap)
    C.nextHopAt = os.clock() + 15
    C.hops += 1
    Teleport:TeleportToPlaceInstance(game.PlaceId, destination, player)
end

task.spawn(function()
    while G.FoccusFragmentCollector == C do
        local ok, err = pcall(function()
            local activeFarm=G.FoccusAnimeBreaker
            local higher = G.FoccusHogyokuCollector
            if higher and higher.enabled and higher.collecting then
                C.collecting = false
                C.nextHopAt = os.clock() + 3
                return
            end
            if activeFarm and activeFarm.ghouls and activeFarm.ghouls.active then
                C.collecting=false
                C.nextHopAt=os.clock()+3
                return
            end
            if not C.enabled or not Library.PlayerData then
                C.target = nil
                C.confirmUntil = nil
                C.collecting = false
                C.scanReady = false
                C.leavingMode = false
                return
            end
            local character = player.Character
            local root = character and character:FindFirstChild("HumanoidRootPart")
            local humanoid = character and character:FindFirstChildOfClass("Humanoid")
            if not root or not humanoid or humanoid.Health <= 0 then
                C.collecting = C.target ~= nil
                C.scanReady = false
                return
            end

            if not C.scanReady then
                C.scanReady = true
                C.nextHopAt = os.clock() + 3
            end

            if C.target and count() > C.before then
                C.collected += count() - C.before
                C.ignoreTarget = C.target
                C.target, C.confirmUntil = nil, nil
                C.collecting = false
                C.confirmed = true
                C.nextHopAt = os.clock() + 1
            end

            if C.confirmed then
                C.collecting = false
                if C.serverHop then
                    if os.clock() >= C.nextHopAt then hop() end
                else
                    C.confirmed = false
                end
                return
            end

            if C.ignoreTarget and not valid(C.ignoreTarget) then C.ignoreTarget = nil end

            if C.target and not valid(C.target) then
                C.confirmUntil = C.confirmUntil or (os.clock() + 3)
                if os.clock() < C.confirmUntil then
                    C.collecting = true
                    return
                end
                C.target, C.confirmUntil = nil, nil
                C.collecting = false
            end

            if not C.target then
                C.target = findNearest(root)
                if C.target then
                    C.before = count()
                    C.nextPromptAt = 0
                    C.nextHopAt = os.clock() + 3
                end
            end

            local target = C.target
            if target then
                C.collecting = true
                local farm = G.FoccusAnimeBreaker
                if farm then
                    farm.target = nil
                    farm.farmContext = nil
                    farm.rangePosition = nil
                end
                local mode = player:GetAttribute("Mode")
                if mode then
                    C.leavingMode = true
                    C.resumeWorldAt = nil
                    if farm then farm.status = "Leaving " .. tostring(mode) .. " for Commandment Fragment" end
                    if os.clock() >= (C.nextQuitAt or 0) then
                        C.nextQuitAt = os.clock() + 2
                        Library.Remote:Fire("GamemodeSystem", "Quit")
                    end
                    return
                end
                if C.leavingMode then
                    C.resumeWorldAt = C.resumeWorldAt or (os.clock() + 1)
                    if farm then farm.status = "Waiting for world after gamemode" end
                    if os.clock() < C.resumeWorldAt then return end
                    C.leavingMode = false
                    C.resumeWorldAt = nil
                end
                if farm then farm.status = "Collecting Commandment Fragment" end
                local p = point(target)
                if not p then return end
                local destination = p + Vector3.new(0, 2, 0)
                if (root.Position - destination).Magnitude > 2 then
                    root.CFrame = CFrame.new(destination)
                    root.AssemblyLinearVelocity = Vector3.zero
                end
                local prompt = target:FindFirstChildWhichIsA("ProximityPrompt", true)
                if prompt and prompt.Enabled and os.clock() >= C.nextPromptAt then
                    C.nextPromptAt = os.clock() + math.max(0.75, prompt.HoldDuration + 0.3)
                    if type(fireproximityprompt) == "function" then
                        fireproximityprompt(prompt)
                    else
                        prompt:InputHoldBegin()
                        task.wait(prompt.HoldDuration + 0.1)
                        prompt:InputHoldEnd()
                    end
                end
                return
            end

            C.collecting = false
            C.leavingMode = false
            C.resumeWorldAt = nil
            if player:GetAttribute("Mode") then
                C.nextHopAt = os.clock() + 3
                return
            end
            if C.serverHop and os.clock() >= C.nextHopAt then hop() end
        end)
        C.error = not ok and tostring(err) or nil
        if not ok then C.nextHopAt = os.clock() + 5 end
        task.wait(ok and 0.2 or 1)
    end
end)
]==]

    local G = getgenv()
    local collector = G.FoccusFragmentCollector
    G.FoccusFragmentWorkerSource = source
    if not collector or not collector.enabled or collector.priorityVersion ~= 2 then
        G.FoccusFragmentRestore = collector and collector.enabled or false
        G.FoccusFragmentHopRestore = collector and collector.serverHop or false
        G.FoccusFragmentVisited = nil
        assert(loadstring(source))()
        self.setIdentity(8)
        collector = G.FoccusFragmentCollector
    end
    local state = self.state
    state.fragmentCollector = collector
    self.tabs.farming:AddSection("Collectibles")
    state.controls.autoCollectFragments = self.tabs.farming:AddToggle({
        Title = "Auto Collect Commandment Fragments",
        Description = "Pauses farming, leaves any gamemode and confirms fragment pickup before resuming.",
        Default = collector.enabled,
        Callback = function(enabled)
            collector.enabled = enabled
            collector.nextHopAt = os.clock() + 3
            collector.target = nil
            collector.confirmUntil = nil
            collector.confirmed = false
            collector.collecting = false
            collector.ignoreTarget = nil
            collector.leavingMode = false
            collector.resumeWorldAt = nil
            collector.nextQuitAt = 0
        end,
    })
    state.controls.fragmentServerHop = self.tabs.farming:AddToggle({
        Title = "Server Hop for Commandment Fragments",
        Description = "When auto collect is on, changes servers after pickup or when none is found.",
        Default = collector.serverHop,
        Callback = function(enabled)
            collector.serverHop = enabled
            collector.nextHopAt = os.clock() + 3
            if not enabled then
                collector.confirmed = false
            end
        end,
    })
    self.window.Gui.Destroying:Connect(function()
        collector.enabled = false
        collector.collecting = false
    end)
end

function Runtime:buildAutoCollectHogyoku()
    local source = [==[
local G = getgenv()
local old = G.FoccusHogyokuCollector
if old then old.enabled = false end

local Players = game:GetService("Players")
local Collection = game:GetService("CollectionService")
local HttpService = game:GetService("HttpService")
local Teleport = game:GetService("TeleportService")
local player = Players.LocalPlayer
local setIdentity = setthreadidentity or setidentity
if setIdentity then setIdentity(2) end
local Library = require(game:GetService("ReplicatedStorage"):WaitForChild("Framework"):WaitForChild("Library"))
local SpawnItemService = Library:GetService("SpawnItemService")
local seen = {}
local saved = G.FoccusHogyokuVisited
if type(saved) == "string" then
    local ok, ids = pcall(HttpService.JSONDecode, HttpService, saved)
    if ok and type(ids) == "table" then
        for _, id in ipairs(ids) do
            if type(id) == "string" then seen[id] = true end
        end
    end
end
G.FoccusHogyokuVisited = nil
local C = {
    priorityVersion = 2,
    enabled = G.FoccusHogyokuRestore == true,
    serverHop = G.FoccusHogyokuHopRestore == true,
    seen = seen,
    target = nil,
    scanReady = false,
    nextHopAt = os.clock() + 3,
    nextPromptAt = 0,
    collected = 0,
    hops = 0,
}
G.FoccusHogyokuRestore = nil
G.FoccusHogyokuHopRestore = nil
G.FoccusHogyokuCollector = C
seen[game.JobId] = true

local function count()
    local data = Library.PlayerData
    return tonumber(data and data.Items and data.Items.HogyokuShard) or 0
end

local function point(item)
    if item:IsA("BasePart") then return item.Position end
    if item:IsA("Model") then return item:GetPivot().Position end
    local part = item:FindFirstChildWhichIsA("BasePart", true)
    return part and part.Position or nil
end

local function valid(item)
    if not item or not item.Parent or not Collection:HasTag(item, "SpawnItem") then return false end
    if item:GetAttribute("SpawnId") ~= "Hogyoku"
        or item:GetAttribute("Type") ~= "HogyokuShard"
        or item:GetAttribute("OwnerId") ~= player.UserId then return false end
    if item:GetAttribute("Forced") == true then return true end
    local data = Library.PlayerData
    if not data then return false end
    local ok, visible = pcall(SpawnItemService.CanSee, player, data,
        "Hogyoku", "HogyokuShard", item:GetAttribute("Seed"))
    return ok and visible == true
end

local function findNearest(root)
    local best, distance = nil, math.huge
    for _, item in ipairs(Collection:GetTagged("SpawnItem")) do
        if item ~= C.ignoreTarget and valid(item) then
            local p = point(item)
            if p then
                local d = (root.Position - p).Magnitude
                if d < distance then best, distance = item, d end
            end
        end
    end
    return best
end

local function requestServers(url)
    local requestFn = request or http_request or (syn and syn.request)
    if type(requestFn) == "function" then
        local response = requestFn({Url = url, Method = "GET"})
        if response and tonumber(response.StatusCode) == 200 then return response.Body end
        error("Server list HTTP " .. tostring(response and response.StatusCode))
    end
    if setIdentity then setIdentity(8) end
    local ok, body = pcall(function() return game:HttpGet(url) end)
    if setIdentity then setIdentity(2) end
    if not ok then error(body) end
    return body
end

local function nextServer()
    local cursor, available = nil, {}
    for _ = 1, 3 do
        local url = "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100&excludeFullGames=true"
        if cursor then url ..= "&cursor=" .. HttpService:UrlEncode(cursor) end
        local page = HttpService:JSONDecode(requestServers(url))
        for _, server in ipairs(page.data or {}) do
            if type(server.id) == "string" and server.id ~= game.JobId
                and tonumber(server.playing) and tonumber(server.maxPlayers)
                and server.playing < server.maxPlayers then
                available[#available + 1] = server
            end
        end
        if #available >= 20 or not page.nextPageCursor then break end
        cursor = page.nextPageCursor
    end
    if #available == 0 then return nil end
    local fresh = {}
    for _, server in ipairs(available) do
        if not seen[server.id] then fresh[#fresh + 1] = server end
    end
    if #fresh == 0 then
        table.clear(seen)
        seen[game.JobId] = true
        fresh = available
    end
    table.sort(fresh, function(a, b) return a.playing < b.playing end)
    return fresh[math.random(1, math.min(#fresh, 10))].id
end

local function hop()
    local queue = queue_on_teleport or queueonteleport or (syn and syn.queue_on_teleport)
    if type(queue) ~= "function" then error("Executor sem queue_on_teleport") end
    local destination = nextServer()
    if not destination then error("Nenhum servidor publico disponivel") end
    seen[destination] = true
    local ids = {}
    for id in pairs(seen) do ids[#ids + 1] = id end
    while #ids > 80 do table.remove(ids, 1) end
    local bootstrap = "local G=getgenv()\nG.FoccusHogyokuRestore=true\nG.FoccusHogyokuHopRestore=true\n"
        .. "G.FoccusHogyokuVisited=" .. string.format("%q", HttpService:JSONEncode(ids)) .. "\n"
        .. "G.FoccusHogyokuWorkerSource=" .. string.format("%q", G.FoccusHogyokuWorkerSource) .. "\n"
        .. "assert(loadstring(G.FoccusHogyokuWorkerSource))()"
    queue(bootstrap)
    C.nextHopAt = os.clock() + 15
    C.hops += 1
    Teleport:TeleportToPlaceInstance(game.PlaceId, destination, player)
end

task.spawn(function()
    while G.FoccusHogyokuCollector == C do
        local ok, err = pcall(function()
            local activeFarm=G.FoccusAnimeBreaker
            if not C.enabled or not Library.PlayerData or count() >= 100 then
                C.target = nil
                C.confirmUntil = nil
                C.collecting = false
                C.scanReady = false
                C.leavingMode = false
                return
            end
            local character = player.Character
            local root = character and character:FindFirstChild("HumanoidRootPart")
            local humanoid = character and character:FindFirstChildOfClass("Humanoid")
            if not root or not humanoid or humanoid.Health <= 0 then
                C.collecting = C.target ~= nil
                C.scanReady = false
                return
            end

            if not C.scanReady then
                C.scanReady = true
                C.nextHopAt = os.clock() + 3
            end

            if C.target and count() > C.before then
                C.collected += count() - C.before
                C.ignoreTarget = C.target
                C.target, C.confirmUntil = nil, nil
                C.collecting = false
                C.confirmed = true
                C.nextHopAt = os.clock() + 1
            end

            if C.confirmed then
                C.collecting = false
                if C.serverHop then
                    if os.clock() >= C.nextHopAt then hop() end
                else
                    C.confirmed = false
                end
                return
            end

            if C.ignoreTarget and not valid(C.ignoreTarget) then C.ignoreTarget = nil end

            if C.target and not valid(C.target) then
                C.confirmUntil = C.confirmUntil or (os.clock() + 3)
                if os.clock() < C.confirmUntil then
                    C.collecting = true
                    return
                end
                C.target, C.confirmUntil = nil, nil
                C.collecting = false
            end

            if not C.target then
                C.target = findNearest(root)
                if C.target then
                    C.before = count()
                    C.nextPromptAt = 0
                    C.nextHopAt = os.clock() + 3
                end
            end

            local target = C.target
            if target then
                C.collecting = true
                local farm = G.FoccusAnimeBreaker
                if farm then
                    farm.target = nil
                    farm.farmContext = nil
                    farm.rangePosition = nil
                end
                local mode = player:GetAttribute("Mode")
                if mode then
                    C.leavingMode = true
                    C.resumeWorldAt = nil
                    if farm then farm.status = "Leaving " .. tostring(mode) .. " for Hogyoku Shard" end
                    if os.clock() >= (C.nextQuitAt or 0) then
                        C.nextQuitAt = os.clock() + 2
                        Library.Remote:Fire("GamemodeSystem", "Quit")
                    end
                    return
                end
                if C.leavingMode then
                    C.resumeWorldAt = C.resumeWorldAt or (os.clock() + 1)
                    if farm then farm.status = "Waiting for world after gamemode" end
                    if os.clock() < C.resumeWorldAt then return end
                    C.leavingMode = false
                    C.resumeWorldAt = nil
                end
                if farm then farm.status = "Collecting Hogyoku Shard" end
                local p = point(target)
                if not p then return end
                local destination = p + Vector3.new(0, 2, 0)
                if root.Anchored then root.Anchored = false end
                if (root.Position - destination).Magnitude > 2 then
                    root.CFrame = CFrame.new(destination)
                    root.AssemblyLinearVelocity = Vector3.zero
                end
                local prompt = target:FindFirstChildWhichIsA("ProximityPrompt", true)
                if prompt and prompt.Enabled and os.clock() >= C.nextPromptAt then
                    C.nextPromptAt = os.clock() + math.max(0.75, prompt.HoldDuration + 0.3)
                    if type(fireproximityprompt) == "function" then
                        fireproximityprompt(prompt)
                    else
                        prompt:InputHoldBegin()
                        task.wait(prompt.HoldDuration + 0.1)
                        prompt:InputHoldEnd()
                    end
                end
                return
            end

            C.collecting = false
            C.leavingMode = false
            C.resumeWorldAt = nil
            if player:GetAttribute("Mode") then
                C.nextHopAt = os.clock() + 3
                return
            end
            if C.serverHop and os.clock() >= C.nextHopAt then hop() end
        end)
        C.error = not ok and tostring(err) or nil
        if not ok then C.nextHopAt = os.clock() + 5 end
        task.wait(ok and 0.2 or 1)
    end
end)
]==]

    local G = getgenv()
    local collector = G.FoccusHogyokuCollector
    G.FoccusHogyokuWorkerSource = source
    if not collector or not collector.enabled or collector.priorityVersion ~= 2 then
        G.FoccusHogyokuRestore = collector and collector.enabled or false
        G.FoccusHogyokuHopRestore = collector and collector.serverHop or false
        G.FoccusHogyokuVisited = nil
        assert(loadstring(source))()
        self.setIdentity(8)
        collector = G.FoccusHogyokuCollector
    end
    local state = self.state
    state.hogyokuCollector = collector
    state.controls.autoCollectHogyoku = self.tabs.farming:AddToggle({
        Title = "Auto Collect Hogyoku Shards",
        Description = "Highest priority: pauses all farms, leaves any gamemode, collects the ground shard and confirms pickup before resuming.",
        Default = collector.enabled,
        Callback = function(enabled)
            collector.enabled = enabled
            collector.nextHopAt = os.clock() + 3
            collector.target = nil
            collector.confirmUntil = nil
            collector.confirmed = false
            collector.collecting = false
            collector.ignoreTarget = nil
            collector.leavingMode = false
            collector.resumeWorldAt = nil
            collector.nextQuitAt = 0
        end,
    })
    state.controls.hogyokuServerHop = self.tabs.farming:AddToggle({
        Title = "Server Hop for Hogyoku Shards",
        Description = "When auto collect is on, changes servers after pickup or when none is found.",
        Default = collector.serverHop,
        Callback = function(enabled)
            collector.serverHop = enabled
            collector.nextHopAt = os.clock() + 3
            if not enabled then
                collector.confirmed = false
            end
        end,
    })
    self.window.Gui.Destroying:Connect(function()
        collector.enabled = false
        collector.collecting = false
    end)
end

function Runtime:buildTabs()
    self.window:SectionTab("Main")
    self.tabs = {}
    local definitions = {
        {
            "farming",
            "Farming",
            "Worlds, NPCs and Secret bosses",
            "swords",
            { { "Farm" } },
            {
                ["World Farm"] = { "Farm", 1 },
                ["Secret Bosses"] = { "Farm", 2 },
                Collectibles = { "Farm", 3 },
            },
        },
        {
            "modes",
            "Modes",
            "Raids, Portals, Trial and boosts",
            "hourglass",
            { { "Raid" }, { "Portal" }, { "Trial" }, { "Boosts" } },
            {
                Raid = { "Raid", 1 },
                ["Raid Players"] = { "Raid", 2 },
                Portal = { "Portal", 1 },
                ["Portal Players"] = { "Portal", 2 },
                Trial = { "Trial", 1 },
                ["Trial Shop"] = { "Trial", 2 },
                ["Mode Equip Best"] = { "Boosts", 1 },
                ["Mode Boosts"] = { "Boosts", 2 },
            },
        },
        {
            "automation",
            "Automation",
            "Rewards, inventory and weather",
            "settings",
            { { "General" }, { "Visual" }, { "Weather" } },
            {
                General = { "General", 1 },
                Inventory = { "General", 2 },
                Visual = { "Visual", 1 },
                ["Weather Equip Best"] = { "Weather", 1 },
                ["Weather Boosts"] = { "Weather", 2 },
            },
        },
        {
            "halloween",
            "Halloween",
            "Halloween shop, crafting and gachas",
            "gift",
            { { "Shop" }, { "Craft" } },
            {
                ["Halloween Shop"] = { "Shop", 1 },
                ["Halloween Craft"] = { "Craft", 1 },
            },
        },
        {
            "gacha",
            "Gacha",
            "Gachas, fighters and upgrades",
            "rotate-ccw",
            { { "Spin" }, { "Upgrades" } },
            {
                Gacha = { "Spin", 1 },
                Fighters = { "Spin", 2 },
                Upgrades = { "Upgrades", 1 },
                Craft = {
                    "Upgrades",
                    2,
                },
            },
        },
        {
            "config",
            "Config",
            "Save, load and reconnect",
            "settings",
            { { "Settings" } },
            {
                Configurations = { "Settings", 1 },
                Reconnect = { "Settings", 2 },
                ["Auto Execute"] = {
                    "Settings",
                    2,
                },
            },
        },
        {
            "invasion",
            "Marine Invasion",
            "Entry, farming and mode automation",
            "hourglass",
            { { "Invasion" }, { "Automation" }, { "Shop" } },
            {
                ["Marine Invasion"] = { "Invasion", 1 },
                ["Invasion Automation"] = { "Automation", 1 },
                ["Invasion Shop"] = { "Shop", 1 },
            },
        },
        {
            "expedition",
            "Expedition",
            "Harbor automation and item boxes",
            "settings",
            { { "Harbor" }, { "Priorities" }, { "Boxes" } },
            {
                ["Harbor Auto"] = { "Harbor", 1 },
                ["Harbor Priorities"] = { "Priorities", 1 },
                ["Auto Open Boxes"] = { "Boxes", 1 },
            },
        },
        {
            "language",
            "Language",
            "Interface language",
            "settings",
            { { "Language" } },
            {
                Language = { "Language", 1 },
            },
        },
        {
            "alerts",
            "Webhook",
            "Personal event notifications",
            "settings",
            { { "Notifications" } },
            {
                ["Webhook Notifications"] = { "Notifications", 1 },
                ["Discord Mentions"] = { "Notifications", 1 },
            },
        },
        {
            "webhook",
            "Webhook",
            "Weather alerts and Discord mentions",
            "settings",
            { { "Weather" } },
            { ["Weather Webhook"] = { "Weather", 1 } },
        },
    }
    local groupSpecs = {
        { "farming", "Farming", { "Farm", "Collectibles" }, "111598016394173" },
        { "raid", "Farm Raid", { "Farm", "Players", "Automation" }, "6031075931", "modes" },
        { "portal", "Farm Portal", { "Farm", "Players", "Automation" }, "6031075927" },
        { "trial", "Farm Trial", { "Farm", "Automation", "Shop" }, "6031071053" },
        { "tower", "Magic Tower", { "Farm", "Players", "Automation" }, "6031075927" },
        { "defense", "Defense", { "Farm", "Players", "Automation" }, "111420325380645" },
        { "invasion", "Marine Invasion", { "Farm", "Automation", "Shop" }, "6031075935" },
        { "expedition", "Expedition", { "Harbor", "Priorities", "Boxes" }, "6031075927" },
        { "halloween", "Halloween", { "Shop", "Craft" }, "6031075938" },
        { "gacha", "Gacha", { "Spin", "Fighters", "Upgrades", "Crafts" }, "6031075938" },
        { "automation", "Automation", { "General", "Inventory", "Visual", "Mode Defaults" }, "6031280882" },
        { "weather", "Weather", { "Automation", "Webhook" }, "6031075925" },
        { "alerts", "Webhook", { "Notifications" }, "6031071053" },
        { "language", "Language", { "Language" }, "6031075938" },
        { "config", "Config", { "Configurations", "Reconnect", "Auto Execute" }, "6031280882" },
    }
    local groups = {}
    local nativeTabs = {}
    for _, spec in ipairs(groupSpecs) do
        local parent = spec[5] or spec[1]
        local native = nativeTabs[parent]
        if not native then
            local title = parent == "modes" and "Game Modes" or spec[2]
            local icon = parent == "modes" and "6031075931" or spec[4]
            native = self.window:AddTab({ Title = title, Icon = icon })
            nativeTabs[parent] = native
        end
        local group = { NativeTab = native, Pages = {} }
        local page = native:AddPage({ Title = spec[2], Single = true })
        for _, name in ipairs(spec[3]) do
            group.Pages[name] = page
        end
        groups[spec[1]] = group
    end
    self.uiGroups = groups
    self:organizeTabs()
    local routes = {
        Language = { "language", "Language", 1 },
        ["Webhook Notifications"] = { "alerts", "Notifications", 1 },
        ["Discord Mentions"] = { "alerts", "Notifications", 1 },
        ["World Farm"] = { "farming", "Farm", 1 },
        ["Secret Bosses"] = { "farming", "Farm", 2 },
        Collectibles = { "farming", "Collectibles", 1 },
        Raid = { "raid", "Farm", 1 },
        ["Raid Players"] = { "raid", "Players", 1 },
        Portal = { "portal", "Farm", 1 },
        ["Portal Players"] = { "portal", "Players", 1 },
        Trial = { "trial", "Farm", 1 },
        ["Trial Shop"] = { "trial", "Shop", 1 },
        ["Magic Tower"] = { "tower", "Farm", 1 },
        ["Tower Players"] = { "tower", "Players", 1 },
        ["Tower Automation"] = { "tower", "Automation", 1 },
        Defense = { "defense", "Farm", 1 },
        ["Defense Players"] = { "defense", "Players", 1 },
        ["Defense Automation"] = { "defense", "Automation", 1 },
        ["Marine Invasion"] = { "invasion", "Farm", 1 },
        ["Invasion Automation"] = { "invasion", "Automation", 1 },
        ["Invasion Shop"] = { "invasion", "Shop", 1 },
        ["Mode Equip Best"] = { "automation", "Mode Defaults", 1 },
        ["Mode Boosts"] = { "automation", "Mode Defaults", 2 },
        General = { "automation", "General", 1 },
        Inventory = { "automation", "Inventory", 1 },
        Visual = { "automation", "Visual", 1 },
        ["Weather Equip Best"] = { "weather", "Automation", 1 },
        ["Weather Boosts"] = { "weather", "Automation", 2 },
        ["Weather Webhook"] = { "weather", "Webhook", 1 },
        ["Halloween Shop"] = { "halloween", "Shop", 1 },
        ["Halloween Craft"] = { "halloween", "Craft", 1 },
        Gacha = { "gacha", "Spin", 1 },
        Fighters = { "gacha", "Fighters", 1 },
        Upgrades = { "gacha", "Upgrades", 1 },
        Craft = { "gacha", "Crafts", 1 },
        Configurations = { "config", "Configurations", 1 },
        Reconnect = { "config", "Reconnect", 1 },
        ["Auto Execute"] = { "config", "Auto Execute", 1 },
        ["Harbor Auto"] = { "expedition", "Harbor", 1 },
        ["Harbor Priorities"] = { "expedition", "Priorities", 1 },
        ["Auto Open Boxes"] = { "expedition", "Boxes", 1 },
    }
    local controlRoutes = {
        ["Raid Equip Best"] = { "raid", "Automation", 1 },
        ["Raid Boosts"] = { "raid", "Automation", 2 },
        ["Portal Equip Best"] = { "portal", "Automation", 1 },
        ["Portal Boosts"] = { "portal", "Automation", 2 },
        ["Trial Equip Best"] = { "trial", "Automation", 1 },
        ["Trial Boosts"] = { "trial", "Automation", 2 },
    }
    self.layoutRoutes = { sections = routes, controls = controlRoutes }
    for _, definition in ipairs(definitions) do
        local defaultKey = definition[1] == "modes" and "raid"
            or definition[1] == "webhook" and "weather"
            or definition[1]
        local adapter = {
            NativeTab = groups[defaultKey].NativeTab,
            routes = definition[6],
            column = 1,
            section = "Default",
            legacyPage = definition[5][1][1],
        }
        local _, firstPage = next(groups[defaultKey].Pages)
        adapter.current = firstPage
        function adapter:RouteSection(title)
            local old = self.routes[title]
            if old then
                self.legacyPage = old[1]
                self.legacyColumn = old[2]
            end
            local route = routes[title]
            if route then
                self.current = groups[route[1]].Pages[route[2]]
                self.column = route[3]
            end
            self.section = title
        end
        function adapter:AddSection(options)
            options = type(options) == "table" and table.clone(options) or { Title = options }
            self:RouteSection(options.Title)
            options.Column = self.column
            return self.current:AddSection(options)
        end
        for _, method in ipairs({
            "AddToggle",
            "AddDropdown",
            "AddInput",
            "AddButton",
            "AddSlider",
            "AddParagraph",
        }) do
            adapter[method] = function(view, options)
                options = table.clone(options)
                -- Preserve legacy flags so moving controls does not reset saved selections.
                options.Flag = options.Flag
                    or definition[1]
                        .. "."
                        .. view.legacyPage
                        .. "."
                        .. view.section
                        .. "."
                        .. tostring(options.Title)
                local destination = view.current
                local route = definition[1] == "modes" and controlRoutes[options.Title]
                if route then
                    local group = groups[route[1]]
                    destination = group.Pages[route[2]]
                    if not group.automationSection then
                        destination:AddSection({ Title = "Automation", Column = 1 })
                        group.automationSection = true
                    end
                end
                options.Column = options.Column or (route and route[3]) or view.column
                local callback = options.Callback
                if callback then
                    options.Callback = function(...)
                        self.setIdentity(8)
                        local result = table.pack(pcall(callback, ...))
                        -- Game callbacks may lower identity; restore it before UI rendering continues.
                        self.setIdentity(8)
                        if not result[1] then
                            error(result[2], 0)
                        end
                        return table.unpack(result, 2, result.n)
                    end
                end
                return destination[method](destination, options)
            end
        end
        self.tabs[definition[1]] = adapter
    end
end

function Runtime:organizeTabs()
    if self.window.IsZeen then return end
    local order = {
        "farming",
        "raid",
        "portal",
        "trial",
        "tower",
        "defense",
        "invasion",
        "expedition",
        "halloween",
        "gacha",
        "automation",
        "weather",
        "alerts",
        "language",
        "config",
    }
    local seen, rails = {}, {}
    local index = 0
    for _, key in ipairs(order) do
        local group = self.uiGroups[key]
        local tab = group and group.NativeTab
        local icon = tab and tab.native and tab.native.Icon
        if icon and not seen[icon] then
            seen[icon] = true
            index += 1
            local position = UDim2.fromOffset(34, 24 + (index - 1) * 48)
            icon.LayoutOrder = index
            icon.Size = UDim2.fromOffset(32, 34)
            icon.Position = position
            rails[icon.Parent] = index
            if self.tabOrderConnections and self.tabOrderConnections[icon] then
                self.tabOrderConnections[icon]:Disconnect()
            end
            self.tabOrderConnections = self.tabOrderConnections or {}
            self.tabOrderConnections[icon] = icon:GetPropertyChangedSignal("Position"):Connect(function()
                if icon.Parent and icon.Position ~= position then
                    icon.Position = position
                end
            end)
            if not icon:GetAttribute("ZeenOrderCleanup") then
                icon:SetAttribute("ZeenOrderCleanup", true)
                icon.Destroying:Connect(function()
                    local connection = self.tabOrderConnections[icon]
                    if connection then
                        connection:Disconnect()
                        self.tabOrderConnections[icon] = nil
                    end
                end)
            end
        end
    end
    for rail, count in pairs(rails) do
        if rail:IsA("ScrollingFrame") then
            rail.CanvasSize = UDim2.fromOffset(0, count * 48)
            rail.CanvasPosition = Vector2.zero
        end
    end
end

function Runtime:buildFarmUI()
    local Library = self.Library
    local maps = self.maps
    local enemies = self.enemies
    local window = self.window
    local state = self.state
    local secretBossList = self.secretBossList
    local toggle = self.toggle
    local main = self.tabs.farming
    main:AddSection("World Farm")
    local codes = {
        "3MVISITS",
        "30KFAVORITES",
        "40KFAVORITES",
        "CLASSTREE",
        "SORRYFORSHUTDOWN",
        "10KCCU",
        "2MVISITS",
        "20KFAVORITES",
        "NEWPORTAL",
        "NEWSHADOW",
        "8KCCU",
        "7KCCU",
        "500KVISITS",
        "750KVISITS",
        "10KFAVORITES",
        "NEWTOTEM",
        "GUILDFIXES",
        "6KCCU",
        "100KVISITS",
        "200KVISITS",
        "300KVISITS",
        "SHUTDOWN",
        "RELEASE",
        "5KPLAYERS",
        "5KFAVS",
    }
    state.redeemCodes = { busy = false, sent = 0 }
    state.redeemButton = main:AddButton({
        Title = "Redeem All Codes",
        Description = "Redeem all " .. #codes .. " listed codes once per click. The game checks validity.",
        Callback = function()
            local redeem = state.redeemCodes
            if redeem.busy then
                return
            end
            redeem.busy = true
            redeem.sent = 0
            redeem.error = nil
            task.spawn(function()
                self.setIdentity(2)
                local ok, err = pcall(function()
                    for _, code in ipairs(codes) do
                        if not state.running then
                            break
                        end
                        Library.Remote:Fire("CodeSystem", "Use", code)
                        redeem.sent += 1
                        task.wait(0.75)
                    end
                end)
                redeem.busy = false
                redeem.error = not ok and tostring(err) or nil
                if state.running then
                    self.setIdentity(8)
                    window:Notify({
                        Title = "Redeem Codes",
                        Description = ok
                                and (tostring(redeem.sent) .. " codes sent. Check game messages for redemption results.")
                            or redeem.error,
                        Duration = 5,
                    })
                end
            end)
        end,
    })
    local worldOptions = {}
    for id, info in pairs(maps) do
        local hasEnemies = false
        for _, enemy in pairs(enemies) do
            if enemy.Map == id then
                hasEnemies = true
                break
            end
        end
        if hasEnemies and not info.Hide then
            table.insert(worldOptions, {
                Title = info.Name or id,
                Value = id,
                Description = Library.PlayerData.UnlockedMap[id] and "Unlocked" or "World locked",
                Order = info.Order or 999,
            })
        end
    end
    table.sort(worldOptions, function(a, b)
        return a.Order < b.Order
    end)
    state.world = worldOptions[1] and worldOptions[1].Value
    local npcDropdown, priorityDropdown, toggle
    local function npcOptions()
        local result = {}
        for id, info in pairs(enemies) do
            if info.Map == state.world then
                table.insert(
                    result,
                    { Title = info.Name or id, Description = id, Value = id, Order = info.Order or 999 }
                )
            end
        end
        table.sort(result, function(a, b)
            if a.Order == b.Order then
                return a.Title < b.Title
            end
            return a.Order < b.Order
        end)
        return result
    end
    local function refreshPriority()
        if not priorityDropdown then
            return
        end
        local options = { { Title = "None", Value = "__none" } }
        for _, option in ipairs(npcOptions()) do
            if state.selected[option.Value] then
                table.insert(options, option)
            end
        end
        if not state.selected[state.priorityEnemy] then
            state.priorityEnemy = nil
        end
        priorityDropdown:Reload(options)
        priorityDropdown:Set(state.priorityEnemy or "__none")
    end
    local worldDropdown = main:AddDropdown({
        Title = "World",
        Description = "Choose the NPC world",
        Multi = false,
        Default = state.world,
        Options = worldOptions,
        Callback = function(value)
            state.world = value
            state.target = nil
            state.selected = {}
            if npcDropdown then
                npcDropdown:Reload(npcOptions())
                npcDropdown:Set({})
            end
            refreshPriority()
        end,
    })
    npcDropdown = main:AddDropdown({
        Title = "NPCs",
        Description = "Choose one or more enemies",
        Placeholder = "Select NPCs",
        Multi = true,
        Default = {},
        Options = npcOptions(),
        Callback = function(values)
            state.selected = {}
            for _, id in ipairs(values) do
                state.selected[id] = true
            end
            state.target = nil
            refreshPriority()
        end,
    })
    priorityDropdown = main:AddDropdown({
        Title = "Priority Enemy",
        Description = "Prefer this NPC when choosing the next target. Select NPCs above first.",
        Multi = false,
        Default = "__none",
        Options = { { Title = "None", Value = "__none" } },
        Callback = function(value)
            state.priorityEnemy = value ~= "__none" and state.selected[value] and value or nil
            state.target = nil
        end,
    })
    toggle = main:AddToggle({
        Title = "Auto Farm Mob",
        Description = "Teleport, attack and repeat until disabled",
        Default = false,
        Callback = function(enabled)
            state.enabled = enabled
            state.target = nil
            state.status = enabled and "Searching for NPCs" or "Disabled"
        end,
    })
    state.controls =
        { world = worldDropdown, npcs = npcDropdown, priorityEnemy = priorityDropdown, toggle = toggle }
    state.worldBoss =
        { enabled = false, active = false, target = nil, nextTravel = 0, nextQuit = 0, pausedAuto = {} }
    main:AddSection("World Boss")
    state.controls.autoFarmWorldBoss = main:AddToggle({
        Title = "Auto Farm World Boss",
        Description = "Highest priority: stops other farms, defeats Pumpkin Boss when it spawns, then resumes them.",
        Default = false,
        Callback = function(value)
            state.worldBoss.enabled = value
            if not value then
                state.worldBoss.active = false
                state.worldBoss.target = nil
                state.target = nil
                state.farmContext = nil
                self:restoreWorldBossAutos()
            end
        end,
    })
    window.Gui.Destroying:Connect(function()
        task.spawn(function()
            self.setIdentity(2)
            self:restoreWorldBossAutos()
        end)
    end)
    main:AddSection("Secret Bosses")
    state.secretBosses = { enabled = false, cursor = 1, current = nil }
    local secretBossList = {}
    local secretBossIds = {}
    for id, enemy in pairs(enemies) do
        if enemy.Rarity == "Secret" and enemy.Type == "Normal" then
            table.insert(secretBossList, { id = id, world = enemy.Map, type = "Normal" })
            secretBossIds[id] = true
        end
    end
    for id, enemy in pairs(enemies) do
        local idText = string.lower(tostring(id))
        local nameText = string.lower(tostring(enemy.Name or ""))
        if
            not secretBossIds[id]
            and (
                id == "KaidoDemon"
                or idText:find("beast demon", 1, true)
                or nameText:find("beast demon", 1, true)
            )
        then
            table.insert(secretBossList, { id = id, world = enemy.Map, type = enemy.Type or "Normal" })
            break
        end
    end
    table.sort(secretBossList, function(a, b)
        local aMap, bMap = maps[a.world], maps[b.world]
        local ao, bo = aMap and aMap.Order or 0, bMap and bMap.Order or 0
        return ao == bo and a.id < b.id or ao < bo
    end)
    local allSecretBosses = {}
    local secretBossOptions = {}
    for _, entry in ipairs(secretBossList) do
        table.insert(allSecretBosses, entry)
        table.insert(
            secretBossOptions,
            {
                Title = entry.id .. " - " .. ((enemies[entry.id] or self.globalBossData[entry.id]).Name or entry.id),
                Value = entry.id,
            }
        )
    end
    state.controls.secretBossSelection = main:AddDropdown({
        Title = "Select Secret Bosses",
        Description = "Empty selection farms all Secret bosses.",
        Placeholder = "All Secret Bosses",
        Multi = true,
        Default = {},
        Options = secretBossOptions,
        Callback = function(values)
            local chosen = {}
            for _, id in ipairs(values) do
                chosen[id] = true
            end
            table.clear(secretBossList)
            for _, entry in ipairs(allSecretBosses) do
                if #values == 0 or chosen[entry.id] then
                    table.insert(secretBossList, entry)
                end
            end
            state.secretBosses.selection = values
            state.secretBosses.cursor = 1
            state.secretBosses.current = nil
            state.secretBosses.scan = nil
            state.target = nil
            state.farmContext = nil
        end,
    })
    state.controls.secretBosses = main:AddToggle({
        Title = "Auto Farm Secret Bosses",
        Description = "Cycle through every available Secret boss in unlocked worlds",
        Default = false,
        Callback = function(value)
            state.secretBosses.enabled = value
            state.secretBosses.current = nil
            state.secretBosses.scan = nil
            state.target = nil
        end,
    })
    self.secretBossList = secretBossList
    self.toggle = toggle
end

function Runtime:buildModes()
    local Library = self.Library
    local player = self.player
    local enemies = self.enemies
    local raids = self.raids
    local window = self.window
    local state = self.state
    local raidState = self.raidState
    local trialState = self.trialState
    local ticketEnemies = self.ticketEnemies
    state.raid = { id = "DBZ", enter = false, farm = false, leave = false, wave = 10, nextAction = 0 }
    state.raid.waitTickets = false
    state.raid.ticketAmount = 1
    state.raid.ticketBatchReady = false
    local raidState = state.raid
    local gamemode = self.tabs.modes
    gamemode:AddSection("Raid")
    local raidOptions, ticketEnemies = {}, {}
    for id, raid in pairs(raids) do
        table.insert(raidOptions, { Title = raid.Name, Value = id, Order = raid.Order or 999 })
        ticketEnemies[id] = {}
        for enemyId, enemy in pairs(enemies) do
            for _, drop in pairs(enemy.Drops or {}) do
                if drop.Id == raid.RequiredItem and (tonumber(drop.Chance) or 0) > 0 then
                    ticketEnemies[id][enemyId] = true
                end
            end
        end
    end
    table.sort(raidOptions, function(a, b)
        return a.Order < b.Order
    end)
    state.controls.raid = gamemode:AddDropdown({
        Title = "Select Raid",
        Description = "Choose a raid",
        Multi = false,
        Default = raidState.id,
        Options = raidOptions,
        Callback = function(id)
            raidState.id = id
            raidState.ticketBatchReady = false
            raidState.nextAction = 0
            raidState.menuFor = nil
            state.target = nil
        end,
    })
    state.controls.enterRaid = gamemode:AddToggle({
        Title = "Auto Enter Raid",
        Description = "Use a ticket or farm enemies that drop it",
        Default = false,
        Callback = function(value)
            raidState.enter = value
            raidState.ticketBatchReady = false
            raidState.nextAction = 0
            raidState.menuFor = nil
            state.target = nil
        end,
    })
    state.controls.raidWaitTickets = gamemode:AddToggle({
        Title = "Wait for Tickets Before Starting",
        Description = "With Auto Enter Raid enabled, collect the selected amount, run raids, then refill when tickets run out.",
        Default = false,
        Callback = function(value)
            raidState.waitTickets = value
            raidState.ticketBatchReady = false
            raidState.nextAction = 0
            state.target = nil
        end,
    })
    local ticketAmountInput
    ticketAmountInput = gamemode:AddInput({
        Title = "Tickets Before Starting (1-250)",
        Default = "1",
        Placeholder = "1-250",
        Callback = function(text)
            local amount = tonumber(text)
            if not amount or amount ~= amount or amount < 1 or amount > 250 or amount % 1 ~= 0 then
                if ticketAmountInput then
                    ticketAmountInput:Set(tostring(raidState.ticketAmount), true)
                end
                return
            end
            raidState.ticketAmount = amount
            raidState.ticketBatchReady = false
            raidState.nextAction = 0
            state.target = nil
        end,
    })
    state.controls.raidTicketAmount = ticketAmountInput
    state.controls.farmRaid = gamemode:AddToggle({
        Title = "Auto Farm Raid",
        Description = "Teleport to and attack enemies in your raid",
        Default = false,
        Callback = function(value)
            raidState.farm = value
            state.target = nil
        end,
    })
    local waveInput
    waveInput = gamemode:AddInput({
        Title = "Leave at Wave",
        Description = "Leave when this wave is reached (1-100)",
        Placeholder = "10",
        Default = "10",
        Callback = function(text)
            local number = tonumber(text)
            if number and number == number and number >= 1 and number <= 100 and number % 1 == 0 then
                raidState.wave = number
            else
                if waveInput then
                    waveInput:Set(tostring(raidState.wave), true)
                end
                window:Notify({
                    Title = "Invalid wave",
                    Description = "Enter a whole number from 1 to 100.",
                    Duration = 3,
                })
            end
        end,
    })
    state.controls.leaveWave = waveInput
    state.controls.leaveRaid = gamemode:AddToggle({
        Title = "Auto Leave",
        Description = "Leave the selected raid at the configured wave",
        Default = false,
        Callback = function(value)
            raidState.leave = value
        end,
    })
    state.fullAutoRaid = { enabled = false, phase = "raids", targetTickets = 250, cursor = 1, activeId = nil }
    local fullAuto = state.fullAutoRaid
    state.controls.fullAutoRaid = gamemode:AddToggle({
        Title = "Full Auto Raid",
        Description = "Runs every raid with tickets. When all tickets end, farms every ticket to 250, then repeats.",
        Default = false,
        Callback = function(value)
            fullAuto.enabled = value
            fullAuto.phase = "raids"
            fullAuto.cursor = 1
            fullAuto.activeId = nil
            raidState.nextAction = 0
            state.target = nil
        end,
    })
    state.ticketEnemies = ticketEnemies
    self:buildRoomControls("Raid")
    state.portal = {
        rank = nil,
        ranks = {},
        rankCursor = 1,
        open = false,
        farm = false,
        leave = false,
        wave = 100,
        nextAction = 0,
        startAt = 0,
        wasInPortal = false,
    }
    local portalState = state.portal
    self.setIdentity(2)
    local portalData = Library:GetData("GamemodeData").Portal or {}
    self.setIdentity(8)
    self.portals = portalData
    local portalOptions = {}
    for id, portal in pairs(portalData) do
        table.insert(portalOptions, {
            Title = portal.Name or id,
            Value = id,
            Description = "Ticket: " .. tostring(portal.OpenItem),
            Order = portal.Order or 999,
        })
    end
    table.sort(portalOptions, function(a, b)
        return a.Order < b.Order
    end)
    portalState.ranks = { portalOptions[1] and portalOptions[1].Value or nil }
    portalState.rank = portalState.ranks[1]
    gamemode:AddSection("Portal")
    state.controls.portalRank = gamemode:AddDropdown({
        Title = "Select Portal Ranks",
        Description = "Uses every ticket from the weakest selected rank before moving to the next (C, B, A, S).",
        Multi = true,
        Default = portalState.ranks,
        Options = portalOptions,
        Callback = function(values)
            local chosen = {}
            for _, value in ipairs(values or {}) do
                chosen[value] = true
            end
            portalState.ranks = {}
            for _, option in ipairs(portalOptions) do
                if chosen[option.Value] then
                    portalState.ranks[#portalState.ranks + 1] = option.Value
                end
            end
            if #portalState.ranks == 0 and portalOptions[1] then
                portalState.ranks[1] = portalOptions[1].Value
            end
            portalState.rankCursor = 1
            portalState.rank = portalState.ranks[1]
            portalState.nextAction = 0
            state.target = nil
        end,
    })
    state.controls.openPortal = gamemode:AddToggle({
        Title = "Auto Open Portal",
        Description = "Opens the selected Portal Rank whenever its ticket is available.",
        Default = false,
        Callback = function(value)
            portalState.open = value
            portalState.nextAction = 0
            state.target = nil
        end,
    })
    state.controls.farmPortal = gamemode:AddToggle({
        Title = "Auto Farm Portal",
        Description = "Teleports to and attacks enemies inside the selected portal.",
        Default = false,
        Callback = function(value)
            portalState.farm = value
            state.target = nil
        end,
    })
    local portalWaveInput
    portalWaveInput = gamemode:AddInput({
        Title = "Portal Leave at Wave",
        Description = "Leave the Portal at this wave (1-100).",
        Placeholder = "100",
        Default = "100",
        Callback = function(text)
            local wave = tonumber(text)
            if wave and wave == wave and wave >= 1 and wave <= 100 and wave % 1 == 0 then
                portalState.wave = wave
            elseif portalWaveInput then
                portalWaveInput:Set(tostring(portalState.wave), true)
            end
        end,
    })
    state.controls.portalWave = portalWaveInput
    state.controls.leavePortal = gamemode:AddToggle({
        Title = "Auto Leave Portal at Wave",
        Description = "Leave the selected Portal Rank at the configured wave.",
        Default = false,
        Callback = function(value)
            portalState.leave = value
        end,
    })
    self:buildRoomControls("Portal")
    state.trial = {
        enter = false,
        farm = false,
        leave = false,
        wave = 10,
        difficulties = { "Easy", "Medium" },
        nextAction = 0,
        skipUntil = 0,
    }
    local trialState = state.trial
    local trial = gamemode
    trial:AddSection("Trial")
    state.controls.enterTrial = trial:AddToggle({
        Title = "Auto Enter Trial",
        Description = "Join The Hallway when entry opens",
        Default = false,
        Callback = function(value)
            trialState.enter = value
            trialState.nextAction = 0
            trialState.menuOpen = false
            state.target = nil
        end,
    })
    state.controls.trialDifficulty = trial:AddDropdown({
        Title = "Trial Difficulty",
        Description = "Choose Easy, Medium, or both. The first available selected difficulty is used.",
        Placeholder = "Select difficulties",
        Multi = true,
        Default = trialState.difficulties,
        Options = {
            { Title = "Easy", Value = "Easy" },
            { Title = "Medium", Value = "Medium" },
        },
        Callback = function(values)
            trialState.difficulties = {}
            for _, value in ipairs(values) do
                if value == "Easy" or value == "Medium" then
                    table.insert(trialState.difficulties, value)
                end
            end
            trialState.nextAction = 0
            state.target = nil
        end,
    })
    state.controls.farmTrial = trial:AddToggle({
        Title = "Auto Farm Trial",
        Description = "Teleport to and attack enemies in your trial",
        Default = false,
        Callback = function(value)
            trialState.farm = value
            state.target = nil
        end,
    })
    trialState.leaveByDifficulty =
        { Easy = { enabled = false, wave = 10 }, Medium = { enabled = false, wave = 10 } }
    for _, difficulty in ipairs({ "Easy", "Medium" }) do
        local rule = trialState.leaveByDifficulty[difficulty]
        local input
        input = trial:AddInput({
            Title = difficulty .. " Leave Wave",
            Default = "10",
            Finished = true,
            Callback = function(text)
                local value = tonumber(text)
                if value and value == value and value % 1 == 0 and value >= 1 and value <= 50 then
                    rule.wave = value
                elseif input then
                    input:Set(tostring(rule.wave), true)
                end
            end,
        })
        state.controls["trialWave" .. difficulty] = input
        state.controls["leaveTrial" .. difficulty] = trial:AddToggle({
            Title = "Auto Leave " .. difficulty,
            Default = false,
            Callback = function(value)
                rule.enabled = value
            end,
        })
    end
    trial:AddSection("Mode Equip Best")
    local equipOptions = {}
    for id, info in pairs(self.boostData) do
        if type(info) == "table" and info.EquipBest then
            table.insert(equipOptions, { Title = info.Name or id, Value = id, Order = info.Order or 999 })
        end
    end
    table.sort(equipOptions, function(a, b)
        return a.Order < b.Order
    end)
    local modeEquip = {
        enabled = false,
        raid = "Damage",
        trial = "Damage",
        portal = "Damage",
        outside = "Energy",
        previous = "__boot",
        error = nil,
    }
    state.modeEquip = modeEquip
    state.controls.modeEquip = trial:AddToggle({
        Title = "Auto Equip Best",
        Description = "Equips the best full setup once when entering a Raid, Trial or Portal.",
        Default = false,
        Callback = function(value)
            modeEquip.enabled = value
            modeEquip.previous = value and "__boot" or player:GetAttribute("Mode")
        end,
    })
    state.controls.raidEquipBest = trial:AddDropdown({
        Title = "Raid Equip Best",
        Description = "Attribute prioritized when a Raid starts.",
        Multi = false,
        Default = "Damage",
        Options = equipOptions,
        Callback = function(value)
            modeEquip.raid = value
        end,
    })
    state.controls.trialEquipBest = trial:AddDropdown({
        Title = "Trial Equip Best",
        Description = "Attribute prioritized when The Hallway starts.",
        Multi = false,
        Default = "Damage",
        Options = equipOptions,
        Callback = function(value)
            modeEquip.trial = value
        end,
    })
    state.controls.portalEquipBest = trial:AddDropdown({
        Title = "Portal Equip Best",
        Description = "Attribute prioritized when entering a Portal.",
        Multi = false,
        Default = "Damage",
        Options = equipOptions,
        Callback = function(value)
            modeEquip.portal = value
        end,
    })
    state.controls.outsideEquipBest = trial:AddDropdown({
        Title = "After Gamemode Equip Best",
        Description = "Attribute prioritized once after leaving a Raid, Trial or Portal.",
        Multi = false,
        Default = "Energy",
        Options = equipOptions,
        Callback = function(value)
            modeEquip.outside = value
        end,
    })
    task.spawn(function()
        self.setIdentity(2)
        while state.running do
            local ok, err = pcall(function()
                local mode = player:GetAttribute("Mode")
                if modeEquip.enabled and mode ~= modeEquip.previous then
                    local wasInMode = modeEquip.previous == "Raid"
                        or modeEquip.previous == "Time Trial"
                        or modeEquip.previous == "Portal"
                        or modeEquip.previous == "Invasion"
                        or modeEquip.previous == "Tower"
                        or modeEquip.previous == "Defense"
                    local isInMode = mode == "Raid"
                        or mode == "Time Trial"
                        or mode == "Portal"
                        or mode == "Invasion"
                        or mode == "Tower"
                        or mode == "Defense"
                    local aspect = mode == "Raid" and modeEquip.raid
                        or mode == "Time Trial" and modeEquip.trial
                        or mode == "Portal" and modeEquip.portal
                        or mode == "Invasion" and state.invasion and state.invasion.equip
                        or mode == "Tower" and state.tower and state.tower.equip
                        or mode == "Defense" and state.defense and state.defense.equip
                        or wasInMode and not isInMode and modeEquip.outside
                        or nil
                    if aspect and aspect ~= "__none" then
                        local boost = self.MultiplierService:GetBoostName(player, aspect)
                        if boost then
                            Library.Remote:Fire("EquipBestSystem", "Apply", boost)
                        end
                    end
                    modeEquip.previous = mode
                end
            end)
            modeEquip.error = not ok and tostring(err) or nil
            task.wait(ok and 0.25 or 3)
        end
    end)
    trial:AddSection("Mode Boosts")
    self:buildModeBoosts(trial)
    window.Gui.Destroying:Connect(function()
        state.running = false
        state.enabled = false
        state.target = nil
    end)
    self.raidState = raidState
    self.trialState = trialState
    self.ticketEnemies = ticketEnemies
end

function Runtime:buildRoomControls(selectedMode)
    local s, tab = self.state, self.tabs.modes
    s.rooms = s.rooms
        or {
            Raid = { wait = false, min = 2, join = false },
            Portal = {
                wait = false,
                min = 2,
                join = false,
            },
        }
    for _, mode in ipairs({ selectedMode }) do
        local settings = s.rooms[mode]
        tab:AddSection(mode .. " Players")
        s.controls[mode .. "Wait"] = tab:AddToggle({
            Title = "Wait for Players - " .. mode,
            Default = false,
            Description = "Auto Enter/Open creates your room; wait before Start. Includes yourself.",
            Callback = function(value)
                settings.wait = value
            end,
        })
        local input
        input = tab:AddInput({
            Title = mode .. " Minimum Players",
            Default = "2",
            Description = "Total players required before starting, including you.",
            Callback = function(value)
                local n = tonumber(value)
                if n and n >= 1 and n <= self.Players.MaxPlayers and n % 1 == 0 then
                    settings.min = n
                else
                    if input then
                        input:Set(tostring(settings.min), true)
                    end
                end
            end,
        })
        s.controls[mode .. "Players"] = input
        s.controls[mode .. "Join"] = tab:AddToggle({
            Title = "Auto Join Public " .. mode,
            Default = false,
            Description = "Join any public room while it is Opened, before the host starts it.",
            Callback = function(value)
                settings.join = value
            end,
        })
    end
end

function Runtime:roomReady(mode, room)
    local settings = self.state.rooms[mode]
    if not settings.wait then
        return true
    end
    local members = room:FindFirstChild("Players")
    local count = 0
    if members then
        for _ in pairs(members:GetAttributes()) do
            count += 1
        end
    end
    settings.count = count
    if count < settings.min then
        self.state.status = mode .. " waiting for players: " .. count .. "/" .. settings.min
        return false
    end
    return true
end

function Runtime:joinPublicRoom(now)
    local s = self.state
    for _, mode in ipairs({ "Portal", "Raid" }) do
        local settings = s.rooms[mode]
        if settings.join then
            for _, room in ipairs(self.GamemodeService.GetRooms(mode)) do
                local host = room:GetAttribute("HostId")
                if
                    host
                    and host ~= self.player.UserId
                    and room:GetAttribute("Private") == false
                    and room:GetAttribute("Status") == "Opened"
                then
                    if now >= (settings.nextJoin or 0) then
                        settings.nextJoin = now + 2
                        self.Library.Remote:Fire("GamemodeSystem", "Join", mode, host)
                    end
                    s.status = "Joining public " .. mode
                    return true
                end
            end
        end
    end
    return false
end

function Runtime:buildTrialShop()
    local Library = self.Library
    local window = self.window
    local state = self.state
    do
        local s = self.state
        if not s.controls.trialShopBuy then
            local identity = setthreadidentity or setidentity
            identity(2)
            local L = self.Library
            local config = L:GetData("StockShopData")["Time Trial"]
            local items = L:GetData("ItemData")
            local service = L:GetService("StockShopService")
            identity(8)
            local tab = self.tabs.modes
            tab:AddSection("Trial Shop")
            local shop = { enabled = false, items = {}, nextBuy = 0, cursor = 1 }
            s.trialShop = shop
            local options = {}
            for id, entry in pairs(config.Items) do
                table.insert(options, {
                    Title = (items[entry.Id] and items[entry.Id].Name) or entry.Id,
                    Value = id,
                    Description = tostring(entry.Price) .. " Trial Shards",
                    Order = entry.Order or 999,
                })
            end
            table.sort(options, function(a, b)
                return a.Order < b.Order
            end)
            s.controls.trialShopItem = tab:AddDropdown({
                Title = "Select Items",
                Description = "Choose one or more Trial Shop items to buy",
                Placeholder = "Select items",
                Multi = true,
                Default = {},
                Options = options,
                Callback = function(values)
                    shop.items = {}
                    for _, value in ipairs(values) do
                        if config.Items[value] then
                            shop.items[#shop.items + 1] = value
                        end
                    end
                    shop.cursor = 1
                    shop.nextBuy = 0
                end,
            })
            s.controls.trialShopBuy = tab:AddToggle({
                Title = "Auto Buy",
                Description = "Buy one at a time while you have shards and stock is available. No paid restocks.",
                Default = false,
                Callback = function(value)
                    shop.enabled = value
                end,
            })
            task.spawn(function()
                identity(2)
                while s.running do
                    if shop.enabled and #shop.items > 0 and os.clock() >= shop.nextBuy then
                        local ok, err = pcall(function()
                            local itemId = shop.items[shop.cursor]
                            shop.cursor = shop.cursor % #shop.items + 1
                            local entry = config.Items[itemId]
                            local data = L.PlayerData
                            local saved = data.StockShops and data.StockShops["Time Trial"]
                            local stock = entry.Stock
                            if saved and saved.Version == service.GetVersion(config) then
                                stock = saved.Items and saved.Items[itemId] or entry.Stock
                            end
                            local balance = tonumber(data.Items[config.Currency]) or 0
                            if stock > 0 and balance >= entry.Price then
                                shop.nextBuy = os.clock() + 0.5
                                L.Remote:Fire("StockShopSystem", "Buy", "Time Trial", itemId, 1)
                            end
                        end)
                        shop.error = not ok and tostring(err) or nil
                        if not ok then
                            shop.nextBuy = os.clock() + 10
                        end
                    end
                    task.wait(0.1)
                end
            end)
        end
    end
end

function Runtime:buildUtilities()
    local setIdentity = self.setIdentity
    local Players = self.Players
    local player = self.player
    local Library = self.Library
    local AutoService = self.AutoService
    local DailyRewardService = self.DailyRewardService
    local chestData = self.chestData
    local dailyData = self.dailyData
    local timeData = self.timeData
    local battlepassData = self.battlepassData
    local window = self.window
    local state = self.state
    local utilities = self.tabs.automation
    utilities:AddSection("General")
    state.antiAFK = state.antiAFK ~= false
    state.antiAFKVersion = 3
    state.antiAFKNext = math.huge
    if state.antiAFKConnection then
        state.antiAFKConnection:Disconnect()
    end
    if state.antiAFKStop then
        state.antiAFKStop()
    end
    local antiAFKToken = {}
    state.antiAFKToken = antiAFKToken
    local virtualInput = game:GetService("VirtualInputManager")
    local virtualUser = game:GetService("VirtualUser")
    local active = true
    local busy = false
    local lastAttempt = -math.huge
    local function idlePulse()
        if
            not active
            or state.antiAFKToken ~= antiAFKToken
            or not state.running
            or not state.antiAFK
            or busy
        then
            return
        end
        if os.clock() - lastAttempt < 5 then
            return
        end
        busy = true
        lastAttempt = os.clock()
        local ok, err = pcall(function()
            if setIdentity then
                setIdentity(8)
            end
            virtualInput:SendKeyEvent(true, Enum.KeyCode.F8, false, game)
            task.wait(0.1)
            virtualInput:SendKeyEvent(false, Enum.KeyCode.F8, false, game)
        end)
        state.antiAFKMethod = "VirtualInputManager"
        if not ok then
            pcall(function()
                virtualInput:SendKeyEvent(false, Enum.KeyCode.F8, false, game)
            end)
            ok, err = pcall(function()
                virtualUser:CaptureController()
                virtualUser:SetKeyDown("0x77")
                task.wait(0.1)
                virtualUser:SetKeyUp("0x77")
            end)
            state.antiAFKMethod = "VirtualUser"
            if not ok then
                pcall(function()
                    virtualUser:SetKeyUp("0x77")
                end)
            end
        end
        busy = false
        state.antiAFKError = not ok and tostring(err) or nil
        if ok then
            state.antiAFKPulses = (state.antiAFKPulses or 0) + 1
            state.antiAFKLastPulse = os.clock()
        end
    end
    local connection = player.Idled:Connect(function()
        state.antiAFKLastIdle = os.clock()
        idlePulse()
    end)
    state.antiAFKConnection = connection
    state.antiAFKStop = function()
        active = false
        connection:Disconnect()
    end
    if not state.controls.antiAFK then
        state.controls.antiAFK = utilities:AddToggle({
            Title = "Anti-AFK",
            Description = "Send periodic keyboard activity to prevent idle disconnection.",
            Default = state.antiAFK,
            Callback = function(enabled)
                state.antiAFK = enabled
                if enabled then
                    task.spawn(idlePulse)
                end
            end,
        })
    end
    task.spawn(function()
        while active and state.running and state.antiAFKToken == antiAFKToken do
            idlePulse()
            task.wait(45)
        end
    end)
    window.Gui.Destroying:Connect(function()
        active = false
        connection:Disconnect()
    end)
    state.utilities = { rank = false, achievements = false, chests = false, daily = false, hourly = false }
    state.utilityErrors = {}
    local utilityControls = {}
    local utilityDefinitions = {
        {
            "rank",
            "Auto Rank Up",
            "Rank up / rebirth when energy is sufficient. Resets energy according to game rules.",
        },
        { "achievements", "Auto Claim Achievements", "Claim completed achievements automatically" },
        { "chests", "Auto Claim Chests", "Claim eligible VIP, Premium and Group chests when ready" },
        { "daily", "Auto Claim Daily Rewards", "Claim daily rewards when playtime requirements are met" },
        {
            "hourly",
            "Auto Claim / Reset Hour Rewards",
            "Claim available rewards; reset only after all are claimed and the timer allows it",
        },
        {
            "battlepassPremium",
            "Auto Claim Premium Battle Pass",
            "Claim unlocked Premium rewards when you own the pass",
        },
        { "battlepassFree", "Auto Claim Free Battle Pass", "Claim unlocked Free rewards automatically" },
    }
    for _, definition in ipairs(utilityDefinitions) do
        local key = definition[1]
        utilityControls[key] = utilities:AddToggle({
            Title = definition[2],
            Description = definition[3],
            Default = false,
            Callback = function(enabled)
                state.utilities[key] = enabled
                state.utilityErrors[key] = nil
            end,
        })
    end
    state.controls.utilities = utilityControls

    do
        utilities:AddSection("Inventory")
        setIdentity(2)
        local MergeService = Library:GetService("MergeService")
        setIdentity(8)
        local merge = { enabled = false, pending = nil, nextRun = 0, completed = 0 }
        state.autoMergeWeapon = merge
        state.controls.autoMergeWeapon = utilities:AddToggle({
            Title = "Auto Merge Weapon",
            Description = "Merge duplicate weapons into stars. Equipped and locked weapons are never consumed.",
            Default = false,
            Callback = function(enabled)
                merge.enabled = enabled
                if enabled and not merge.pending then
                    merge.nextRun = 0
                end
            end,
        })

        local function updateMerge()
            local data = Library.PlayerData
            if not data or not data.Weapons then
                return
            end
            local now = os.clock()
            if merge.pending then
                local pending = merge.pending
                local weapon = data.Weapons[pending.target]
                if not weapon or MergeService:GetObjectTier("Weapon", weapon) ~= pending.tier then
                    if weapon then
                        merge.completed += 1
                    end
                    merge.pending = nil
                    merge.nextRun = now + 0.5
                    return
                end
                if now < pending.deadline then
                    return
                end
                merge.pending = nil
                merge.nextRun = now + 10
                merge.error = "Merge not confirmed; waiting before retry."
                return
            end
            if not merge.enabled or now < merge.nextRun then
                return
            end
            merge.nextRun = now + 2
            local plan = MergeService:Plan(data, "Weapon")
            for _, action in ipairs(plan) do
                if MergeService:Validate(data, "Weapon", action.Target, action.List) then
                    local tier = MergeService:GetObjectTier("Weapon", data.Weapons[action.Target])
                    merge.pending = { target = action.Target, tier = tier, deadline = now + 10 }
                    Library.Remote:Fire(
                        "MergeSystem",
                        "Make",
                        "Weapon",
                        action.Target,
                        Library:Encode(action.List)
                    )
                    merge.error = nil
                    return
                end
            end
        end

        task.spawn(function()
            setIdentity(2)
            while state.running do
                if merge.enabled or merge.pending then
                    local ok, err = pcall(updateMerge)
                    if not ok then
                        merge.error = tostring(err)
                        merge.nextRun = os.clock() + 10
                    end
                end
                task.wait(0.5)
            end
        end)
    end

    do
        setIdentity(2)
        local MergeService = Library:GetService("MergeService")
        setIdentity(8)
        local merge = { enabled = false, pending = nil, nextRun = 0, completed = 0 }
        state.autoMergeShadow = merge
        state.controls.autoMergeShadow = utilities:AddToggle({
            Title = "Auto Merge Shadows",
            Description = "Merge duplicate Shadows using the game plan; protects locked, equipped and spinning sacrifices.",
            Default = false,
            Callback = function(enabled)
                merge.enabled = enabled
                if enabled and not merge.pending then
                    merge.nextRun = 0
                end
            end,
        })

        local function updateMerge()
            local data = Library.PlayerData
            if not data or not data.Warriors then
                return
            end
            local now = os.clock()
            if merge.pending then
                local pending = merge.pending
                local weapon = data.Warriors[pending.target]
                if not weapon or MergeService:GetObjectTier("Warrior", weapon) ~= pending.tier then
                    if weapon then
                        merge.completed += 1
                    end
                    merge.pending = nil
                    merge.nextRun = now + 0.5
                    return
                end
                if now < pending.deadline then
                    return
                end
                merge.pending = nil
                merge.nextRun = now + 10
                merge.error = "Merge not confirmed; waiting before retry."
                return
            end
            if not merge.enabled or now < merge.nextRun then
                return
            end
            merge.nextRun = now + 2
            local plan = MergeService:Plan(data, "Warrior")
            for _, action in ipairs(plan) do
                local item = data.Warriors[action.Target]
                local info = item and Library:GetData("WarriorData")[item.Id]
                if
                    info
                    and info.Type == "Shadow"
                    and MergeService:Validate(data, "Warrior", action.Target, action.List)
                then
                    local tier = MergeService:GetObjectTier("Warrior", data.Warriors[action.Target])
                    merge.pending = { target = action.Target, tier = tier, deadline = now + 10 }
                    Library.Remote:Fire(
                        "MergeSystem",
                        "Make",
                        "Warrior",
                        action.Target,
                        Library:Encode(action.List)
                    )
                    merge.error = nil
                    return
                end
            end
        end

        task.spawn(function()
            setIdentity(2)
            while state.running do
                if merge.enabled or merge.pending then
                    local ok, err = pcall(updateMerge)
                    if not ok then
                        merge.error = tostring(err)
                        merge.nextRun = os.clock() + 10
                    end
                end
                task.wait(0.5)
            end
        end)
    end

    utilities:AddSection("Visual")
    do
        local s = self.state
        if not s.controls.hidePlayerName then
            local player = game:GetService("Players").LocalPlayer
            local gui = player:WaitForChild("PlayerGui")
            local hidden = false
            local changed = {}
            local function apply()
                local bill = gui:FindFirstChild("Billboards")
                local board = bill and bill:FindFirstChild(player.Name)
                local info = board and board:FindFirstChild("Info")
                local label = info and info:FindFirstChild("PlayerName")
                if label and label:IsA("TextLabel") then
                    if changed[label] == nil then
                        changed[label] = label.Visible
                    end
                    label.Visible = not hidden
                end
                local role = info and info:FindFirstChild("Role")
                if role and role:IsA("TextLabel") then
                    if changed[role] == nil then
                        changed[role] = role.Visible
                    end
                    role.Visible = not hidden
                end
                local guild = board and board:FindFirstChild("Guild")
                if guild and guild:IsA("GuiObject") then
                    if changed[guild] == nil then
                        changed[guild] = guild.Visible
                    end
                    guild.Visible = not hidden
                end
            end
            local childConn = gui.ChildAdded:Connect(function(child)
                if child.Name == "Billboards" then
                    task.defer(apply)
                end
            end)
            local utilities = self.tabs.automation
            s.controls.hidePlayerName = utilities:AddToggle({
                Title = "Hide Player Name",
                Description = "Hide your overhead nickname.",
                Default = false,
                Callback = function(value)
                    hidden = value
                    s.hidePlayerName = value
                    apply()
                end,
            })
            s.hidePlayerNameChanged = changed
            s.hidePlayerNameApply = apply
            apply()
            s.window.Gui.Destroying:Connect(function()
                childConn:Disconnect()
                for label, visible in pairs(changed) do
                    if label.Parent then
                        label.Visible = visible
                    end
                end
            end)
        end
    end
    local utilityActions = {}
    local battlepassPending = {}
    local function claimBattlepass(track, key)
        local data = Library.PlayerData.Battlepass or {}
        for id, definition in pairs(battlepassData) do
            local progress = data[id] and data[id][definition.Season]
            local trackInfo = definition.Types and definition.Types[track]
            if progress and trackInfo and (not trackInfo.ToBuy or progress[track] == true) then
                for tier, rewards in ipairs(definition.Rewards) do
                    if tier > (tonumber(progress.Level) or 0) then
                        break
                    end
                    local claimed = progress.Rewards and progress.Rewards[tostring(tier)]
                    local pendingKey = id .. ":" .. tostring(definition.Season) .. ":" .. tier .. ":" .. track
                    if
                        rewards[track]
                        and not (claimed and claimed[track])
                        and os.clock() >= (battlepassPending[pendingKey] or 0)
                    then
                        if not state.running or not state.utilities[key] then
                            return
                        end
                        battlepassPending[pendingKey] = os.clock() + 15
                        Library.Remote:Fire("BattlepassSystem", "Claim", id, tier, track)
                        return
                    end
                end
            end
        end
    end
    function utilityActions.battlepassPremium()
        claimBattlepass("Premium", "battlepassPremium")
    end
    function utilityActions.battlepassFree()
        claimBattlepass("Free", "battlepassFree")
    end
    function utilityActions.rank()
        local category, kind = AutoService.GetPendingRebirth(Library.PlayerData)
        if category then
            Library.Remote:Fire("RebirthSystem", "Release", category, kind)
        end
    end
    function utilityActions.achievements()
        Library.Remote:Fire("AchievementSystem", "ClaimAll", true)
    end
    function utilityActions.chests()
        local data = Library.PlayerData
        local now = Library.Replicated:GetAttribute("Time") or os.time()
        for _, id in ipairs({ "VIPChest", "PremiumChest", "GroupChest" }) do
            local chest = chestData[id]
            local readyAt = data.Delay and data.Delay[id]
            if chest and readyAt and now >= readyAt and chest.CanClaim(player) then
                if not state.running or not state.utilities.chests then
                    return
                end
                Library.Remote:Fire("ChestSystem", "Claim", id)
            end
        end
    end
    function utilityActions.daily()
        local day = DailyRewardService.CurrentDay()
        for id in pairs(dailyData) do
            local reward = Library.PlayerData.DailyRewards[id]
            if
                reward
                and not reward.Claimed[tostring(day)]
                and DailyRewardService.HasPlaytime(id, day, reward.Time)
            then
                if not state.running or not state.utilities.daily then
                    return
                end
                Library.Remote:Fire("DailyRewardSystem", "Claim", id, day)
            end
        end
    end
    function utilityActions.hourly()
        for id, definition in pairs(timeData) do
            local progress = Library.PlayerData.TimeRewards[id]
            if progress then
                local allClaimed = true
                for index, reward in pairs(definition.Rewards) do
                    if not progress.Claimed[index] then
                        allClaimed = false
                        if progress.Time > reward.Time then
                            if not state.running or not state.utilities.hourly then
                                return
                            end
                            Library.Remote:Fire("TimeRewardSystem", "Claim", id, index)
                        end
                    end
                end
                if allClaimed and progress.Time > definition.ResetTime then
                    if not state.running or not state.utilities.hourly then
                        return
                    end
                    Library.Remote:Fire("TimeRewardSystem", "Reset", id)
                end
            end
        end
    end
    task.spawn(function()
        setIdentity(2)
        local nextRun = {}
        while state.running do
            state.utilityTick = os.clock()
            for key, action in pairs(utilityActions) do
                if
                    state.running
                    and state.utilities[key]
                    and Library.PlayerData
                    and os.clock() >= (nextRun[key] or 0)
                then
                    nextRun[key] = os.clock() + (key == "rank" and 1 or 5)
                    local ok, err = pcall(action)
                    if not ok then
                        state.utilities[key] = false
                        state.utilityErrors[key] = tostring(err)
                        task.defer(function()
                            setIdentity(8)
                            if state.running then
                                utilityControls[key]:Set(false, true)
                                window:Notify({
                                    Title = "Utilities",
                                    Description = key .. " paused: " .. tostring(err),
                                    Duration = 5,
                                })
                            end
                        end)
                    end
                end
            end
            task.wait(0.5)
        end
    end)
    self.utilities = utilities
end

function Runtime:buildReconnect()
    local state, player = self.state, self.player
    local TeleportService = game:GetService("TeleportService")
    local GuiService = game:GetService("GuiService")
    local tab = self.tabs.config
    local reconnect = { enabled = false, attempting = false, nextAttempt = 0, connections = {} }
    state.reconnect = reconnect
    tab:AddSection("Reconnect")
    state.controls.autoReconnect = tab:AddToggle({
        Title = "Auto Reconnect",
        Description = "Reconnects to this experience after a Roblox disconnect.",
        Default = false,
        Callback = function(value)
            reconnect.enabled = value
        end,
    })
    local function reconnectNow(reason)
        if
            not state.running
            or not reconnect.enabled
            or reconnect.attempting
            or os.clock() < reconnect.nextAttempt
        then
            return
        end
        reconnect.attempting = true
        reconnect.nextAttempt = os.clock() + 12
        reconnect.reason = tostring(reason or "Disconnected")
        task.delay(2, function()
            if state.running and reconnect.enabled then
                pcall(function()
                    TeleportService:Teleport(game.PlaceId, player)
                end)
            end
            reconnect.attempting = false
        end)
    end
    reconnect.connections[1] = GuiService.ErrorMessageChanged:Connect(function(message)
        if message and message ~= "" then
            reconnectNow(message)
        end
    end)
    reconnect.connections[2] = TeleportService.TeleportInitFailed:Connect(function(_, result, message)
        reconnect.attempting = false
        reconnect.lastError = tostring(result) .. ": " .. tostring(message)
        task.delay(5, function()
            reconnectNow(reconnect.lastError)
        end)
    end)
    self.window.Gui.Destroying:Connect(function()
        for _, connection in ipairs(reconnect.connections) do
            connection:Disconnect()
        end
    end)
end

function Runtime:buildConfig()
    local state, tab, window = self.state, self.tabs.config, self.window
    local HttpService = game:GetService("HttpService")
    local root = "FoccusAnimeBreaker/Configs"
    local function available()
        return type(writefile) == "function" and type(readfile) == "function" and type(isfile) == "function"
    end
    local function path(name)
        return root .. "/" .. name:gsub("[^%w_%- ]", "") .. ".json"
    end
    local function selected(set)
        local values = {}
        for id, value in pairs(set or {}) do
            if value then
                values[#values + 1] = id
            end
        end
        table.sort(values)
        return values
    end
    local function snapshot()
        return {
            extra = self:snapshotExtra(),
            world = state.world,
            selected = selected(state.selected),
            priorityEnemy = state.priorityEnemy,
            farmMode = state.farmMode,
            secretBosses = state.secretBosses and state.secretBosses.selection or {},
            autoCollectFragments = state.fragmentCollector and state.fragmentCollector.enabled or false,
            fragmentServerHop = state.fragmentCollector and state.fragmentCollector.serverHop or false,
            autoCollectHogyoku = state.hogyokuCollector and state.hogyokuCollector.enabled or false,
            hogyokuServerHop = state.hogyokuCollector and state.hogyokuCollector.serverHop or false,
            rooms = {
                Raid = {
                    wait = state.rooms.Raid.wait,
                    min = state.rooms.Raid.min,
                    join = state.rooms.Raid.join,
                },
                Portal = {
                    wait = state.rooms.Portal.wait,
                    min = state.rooms.Portal.min,
                    join = state.rooms.Portal.join,
                },
            },
            raid = {
                id = state.raid.id,
                enter = state.raid.enter,
                farm = state.raid.farm,
                leave = state.raid.leave,
                wave = state.raid.wave,
                full = state.fullAutoRaid.enabled,
            },
            portal = {
                rank = state.portal.rank,
                ranks = table.clone(state.portal.ranks or {}),
                open = state.portal.open,
                farm = state.portal.farm,
                leave = state.portal.leave,
                wave = state.portal.wave,
            },
            trial = {
                enter = state.trial.enter,
                farm = state.trial.farm,
                leaveByDifficulty = state.trial.leaveByDifficulty,
                difficulties = table.clone(state.trial.difficulties or {}),
            },
            trialShop = { enabled = state.trialShop.enabled, items = state.trialShop.items },
            utilities = state.utilities,
            antiAFK = state.antiAFK,
            autoMergeWeapon = state.autoMergeWeapon and state.autoMergeWeapon.enabled,
            autoMergeShadow = state.autoMergeShadow and state.autoMergeShadow.enabled,
            shadowRoll = state.scrollControl
                and { target = state.scrollControl.shadow, enabled = state.scrollControl.shadowOn },
            modeEquip = state.modeEquip,
            modeBoost = state.modeBoost and {
                enabled = state.modeBoost.enabled,
                raid = state.modeBoost.raid,
                trial = state.modeBoost.trial,
                portal = state.modeBoost.portal,
            },
            weather = state.weatherEquip
                and { enabled = state.weatherEquip.enabled, selected = state.weatherEquip.selected },
            weatherBoost = state.weatherBoost and {
                enabled = state.weatherBoost.enabled,
                weathers = table.clone(state.weatherBoost.weathers),
                boosts = table.clone(state.weatherBoost.boosts),
            },
            autoReconnect = state.reconnect and state.reconnect.enabled,
            weatherWebhook = state.weatherWebhook and {
                enabled = state.weatherWebhook.enabled,
                url = state.weatherWebhook.url,
                userId = state.weatherWebhook.userId,
                ping = selected(state.weatherWebhook.selected),
            },
        }
    end
    local function control(key, value)
        local item = state.controls[key]
        if item and item.Set then
            pcall(function()
                item:Set(value)
            end)
        end
    end
    local function apply(data)
        if type(data) ~= "table" then
            error("Invalid config")
        end
        self:restoreExtra(data.extra)
        if type(data.weatherBoost) == "table" then
            local w = data.weatherBoost
            if type(w.weathers) == "table" then
                control("weatherBoostWeathers", w.weathers)
            end
            if type(w.boosts) == "table" then
                control("weatherBoostItems", w.boosts)
            end
            if type(w.enabled) == "boolean" then
                control("weatherBoostEnabled", w.enabled)
            end
        end
        if type(data.weatherWebhook) == "table" then
            local w = data.weatherWebhook
            control("weatherWebhookUrl", type(w.url) == "string" and w.url or "")
            if type(w.userId) == "string" then
                control("weatherWebhookUser", w.userId)
            end
            if type(w.ping) == "table" then
                control("weatherWebhookPing", w.ping)
            end
            if type(w.enabled) == "boolean" then
                control("weatherWebhookEnabled", w.enabled)
            end
        end
        for _, mode in ipairs({ "Raid", "Portal" }) do
            local room = data.rooms and data.rooms[mode]
            if room then
                if type(room.wait) == "boolean" then
                    control(mode .. "Wait", room.wait)
                end
                if type(room.join) == "boolean" then
                    control(mode .. "Join", room.join)
                end
                if type(room.min) == "number" then
                    control(mode .. "Players", tostring(room.min))
                end
            end
        end
        if data.world then
            control("world", data.world)
        end
        if data.selected then
            control("npcs", data.selected)
        end
        if data.priorityEnemy then
            control("priorityEnemy", data.priorityEnemy)
        end
        if data.farmMode then
            control("farmMode", data.farmMode)
        end
        if data.secretBosses then
            control("secretBossSelection", data.secretBosses)
        end
        if data.autoCollectFragments ~= nil then
            control("autoCollectFragments", data.autoCollectFragments)
        end
        if data.fragmentServerHop ~= nil then
            control("fragmentServerHop", data.fragmentServerHop)
        end
        if data.autoCollectHogyoku ~= nil then
            control("autoCollectHogyoku", data.autoCollectHogyoku)
        end
        if data.hogyokuServerHop ~= nil then
            control("hogyokuServerHop", data.hogyokuServerHop)
        end
        local raid = data.raid or {}
        if raid.id then
            control("raid", raid.id)
        end
        for key, field in pairs({
            enterRaid = "enter",
            farmRaid = "farm",
            leaveRaid = "leave",
            fullAutoRaid = "full",
        }) do
            if raid[field] ~= nil then
                control(key, raid[field])
            end
        end
        if raid.wave then
            state.raid.wave = raid.wave
            control("leaveWave", tostring(raid.wave))
        end
        local portal = data.portal or {}
        if portal.ranks and #portal.ranks > 0 then
            control("portalRank", portal.ranks)
        elseif portal.rank then
            control("portalRank", { portal.rank })
        end
        if portal.open ~= nil then
            control("openPortal", portal.open)
        end
        if portal.farm ~= nil then
            control("farmPortal", portal.farm)
        end
        if portal.leave ~= nil then
            control("leavePortal", portal.leave)
        end
        if portal.wave then
            state.portal.wave = portal.wave
            control("portalWave", tostring(portal.wave))
        end
        local trial = data.trial or {}
        for _, difficulty in ipairs({ "Easy", "Medium" }) do
            local rule = trial.leaveByDifficulty and trial.leaveByDifficulty[difficulty]
            if rule then
                control("trialWave" .. difficulty, tostring(rule.wave or 10))
                control("leaveTrial" .. difficulty, rule.enabled == true)
            elseif trial.leave ~= nil then
                control("trialWave" .. difficulty, tostring(trial.wave or 10))
                control("leaveTrial" .. difficulty, trial.leave == true)
            end
        end
        for key, field in pairs({ enterTrial = "enter", farmTrial = "farm", leaveTrial = "leave" }) do
            if trial[field] ~= nil then
                control(key, trial[field])
            end
        end
        if trial.wave then
            state.trial.wave = trial.wave
            control("trialWave", tostring(trial.wave))
        end
        if type(trial.difficulties) == "table" then
            control("trialDifficulty", trial.difficulties)
        end
        local shop = data.trialShop or {}
        if shop.items then
            control("trialShopItem", shop.items)
        end
        if shop.enabled ~= nil then
            control("trialShopBuy", shop.enabled)
        end
        if data.antiAFK ~= nil then
            control("antiAFK", data.antiAFK)
        end
        if data.autoMergeWeapon ~= nil then
            control("autoMergeWeapon", data.autoMergeWeapon)
        end
        if data.autoMergeShadow ~= nil then
            control("autoMergeShadow", data.autoMergeShadow)
        end
        if data.shadowRoll then
            control("shadowTarget", data.shadowRoll.target)
            control("shadowRoll", data.shadowRoll.enabled == true)
        end
        if data.autoReconnect ~= nil then
            control("autoReconnect", data.autoReconnect)
        end
        for key, value in pairs(data.utilities or {}) do
            if state.controls.utilities and state.controls.utilities[key] then
                control(key, value)
            end
        end
        if data.modeEquip then
            control("portalEquipBest", data.modeEquip.portal or "Damage")
            control("modeEquip", data.modeEquip.enabled)
            control("raidEquipBest", data.modeEquip.raid)
            control("trialEquipBest", data.modeEquip.trial)
            control("outsideEquipBest", data.modeEquip.outside)
        end
        if data.modeBoost then
            control("modeBoost", data.modeBoost.enabled)
            control("raidBoost", data.modeBoost.raid)
            control("trialBoost", data.modeBoost.trial)
            control("portalBoost", data.modeBoost.portal or {})
        end
        if data.weather then
            control("weatherEquip", data.weather.enabled)
            for id, value in pairs(data.weather.selected or {}) do
                control(id == "__none" and "weatherOutside" or "weather_" .. id, value)
            end
        end
    end
    local function list()
        local options = {}
        if available() and isfolder and isfolder(root) then
            for _, file in ipairs(listfiles(root)) do
                local name = file:match("([^/\\]+)%.json$")
                if name then
                    options[#options + 1] = { Title = name, Value = name }
                end
            end
        end
        table.sort(options, function(a, b)
            return a.Title < b.Title
        end)
        return options
    end
    tab:AddSection("Configurations")
    local config = { name = "default", selected = nil, auto = false }
    state.config = config
    state.controls.configName = tab:AddInput({
        Title = "Config Name",
        Description = "Name used when saving.",
        Default = "default",
        Callback = function(value)
            config.name = value
        end,
    })
    local configList = tab:AddDropdown({
        Title = "Config List",
        Description = "Select a configuration to load or delete.",
        Multi = false,
        Options = list(),
        Callback = function(value)
            config.selected = value
        end,
    })
    state.controls.configList = configList
    local function refresh()
        configList:Reload(list())
    end
    tab:AddButton({
        Title = "Save Config",
        Description = "Save all current automation selections and toggles.",
        Callback = function()
            if not available() then
                return window:Notify({
                    Title = "Config",
                    Description = "Executor file APIs are unavailable.",
                    Duration = 4,
                })
            end
            if not isfolder(root) then
                makefolder(root)
            end
            local name = (config.name and config.name ~= "") and config.name or "default"
            writefile(path(name), HttpService:JSONEncode(snapshot()))
            config.selected = name
            refresh()
            window:Notify({ Title = "Config", Description = "Saved: " .. name, Duration = 3 })
        end,
    })
    tab:AddButton({
        Title = "Load Config",
        Description = "Load the selected configuration.",
        Callback = function()
            local name = config.selected or config.name
            if not available() or not name or not isfile(path(name)) then
                return
            end
            local ok, data = pcall(function()
                return HttpService:JSONDecode(readfile(path(name)))
            end)
            if ok then
                apply(data)
                window:Notify({ Title = "Config", Description = "Loaded: " .. name, Duration = 3 })
            end
        end,
    })
    tab:AddButton({
        Title = "Refresh Config List",
        Description = "Refresh saved configuration names.",
        Callback = refresh,
    })
    tab:AddButton({
        Title = "Delete Selected Config",
        Description = "Delete the selected configuration.",
        Callback = function()
            if available() and delfile and config.selected and isfile(path(config.selected)) then
                delfile(path(config.selected))
                refresh()
            end
        end,
    })
    state.controls.configAutoLoad = tab:AddToggle({
        Title = "Set Auto Load Config",
        Description = "Automatically load the selected config next time the script runs.",
        Default = false,
        Callback = function(value)
            config.auto = value
            if available() then
                if not isfolder(root) then
                    makefolder(root)
                end
                if value and config.selected then
                    writefile(root .. "/autoload.txt", config.selected)
                elseif isfile(root .. "/autoload.txt") and delfile then
                    delfile(root .. "/autoload.txt")
                end
            end
        end,
    })
    if not getgenv().ZeenTeleportSettings and available() and isfile(root .. "/autoload.txt") then
        local name = readfile(root .. "/autoload.txt")
        if isfile(path(name)) then
            config.selected = name
            config.name = name
            control("configAutoLoad", true)
            local ok, data = pcall(function()
                return HttpService:JSONDecode(readfile(path(name)))
            end)
            if ok then
                task.defer(apply, data)
            end
        end
    end
end

function Runtime:buildWeatherWebhook()
    local state, tab = self.state, self.tabs.webhook
    local settings = {
        enabled = true,
        url = "",
        userId = "",
        selected = {},
        seen = {},
        queue = {},
        sent = 0,
        baseline = true,
    }
    state.weatherWebhook = settings
    local catalog, options = self.weatherData.List, {}
    for id, info in pairs(catalog) do
        options[#options + 1] = { Title = info.Name or id, Value = id, Order = info.Order or 999 }
    end
    table.sort(options, function(a, b)
        return a.Order < b.Order
    end)
    tab:AddSection("Weather Webhook")
    tab:AddParagraph({
        Title = "All Weather Events",
        Description = "Paste your full Discord webhook URL below. Sends all new weather events to your webhook; weather selection only controls mentions. A blank URL disables delivery.",
    })
    local webhookInput
    webhookInput = tab:AddInput({
        Title = "Discord Webhook URL",
        Flag = "webhook.Weather.Weather Webhook.URL",
        Default = "",
        Placeholder = "https://discord.com/api/webhooks/.../...",
        Callback = function(value)
            local url = tostring(value or ""):match("^%s*(.-)%s*$")
            local host, id, token = url:match("^https://([^/]+)/api/webhooks/(%d+)/([%w_%-]+)$")
            if
                url ~= ""
                and not (
                    (
                        host == "discord.com"
                        or host == "discordapp.com"
                        or host == "canary.discord.com"
                        or host == "ptb.discord.com"
                    )
                    and id
                    and token
                )
            then
                self.window:Notify({
                    Title = "Invalid Webhook URL",
                    Description = "Paste the complete Discord webhook URL, not only its ID.",
                    Duration = 5,
                })
                if webhookInput then
                    webhookInput:Set(settings.url, true)
                end
                return
            end
            if settings.url ~= url then
                table.clear(settings.queue)
                settings.baseline = true
                settings.error = nil
            end
            settings.url = url
            if webhookInput then
                webhookInput:Set(url, true)
            end
        end,
    })
    state.controls.weatherWebhookUrl = webhookInput
    state.controls.weatherWebhookEnabled = tab:AddToggle({
        Title = "Send Weather Alerts",
        Flag = "webhook.Weather.Weather Webhook.Enviar weathers",
        Default = true,
        Callback = function(value)
            settings.enabled = value
            if not value then
                table.clear(settings.queue)
            end
        end,
    })
    local input
    input = tab:AddInput({
        Title = "Discord User ID",
        Default = "",
        Placeholder = "Discord user ID (blank = no ping)",
        Callback = function(value)
            local id = WeatherAlerts.normalizeUser(value)
            if id == nil then
                self.window:Notify({
                    Title = "Invalid Discord ID",
                    Description = "Enter your 17-20 digit Discord user ID, not your username.",
                    Duration = 5,
                })
                if input then
                    input:Set(settings.userId, true)
                end
                return
            end
            settings.userId = id
            if input then
                input:Set(id, true)
            end
        end,
    })
    state.controls.weatherWebhookUser = input
    state.controls.weatherWebhookPing = tab:AddDropdown({
        Title = "Weather Ping Selection",
        Flag = "webhook.Weather.Weather Webhook.Ping nestes weathers",
        Multi = true,
        Default = {},
        Options = options,
        Description = "All other weather alerts are still sent, without a mention.",
        Callback = function(values)
            settings.selected = {}
            for _, id in ipairs(values) do
                if catalog[id] then
                    settings.selected[id] = true
                end
            end
        end,
    })
    task.spawn(function()
        self.setIdentity(2)
        while state.running do
            if self.window.ready then
                local ok = pcall(function()
                    local events = WeatherAlerts.events(
                        self.WeatherService.GetActiveList(),
                        settings.seen,
                        self.WeatherService.GetTime(),
                        settings.baseline or not settings.enabled or settings.url == ""
                    )
                    settings.baseline = false
                    for _, event in ipairs(events) do
                        local info = catalog[event.id]
                        if info and #settings.queue < 32 then
                            settings.queue[#settings.queue + 1] = {
                                url = settings.url,
                                payload = WeatherAlerts.payload(
                                    event,
                                    info.Name,
                                    settings.userId,
                                    settings.selected
                                ),
                                attempts = 0,
                                readyAt = 0,
                            }
                        end
                    end
                end)
                if not ok then
                    settings.error = "Unable to read weather events."
                end
            end
            task.wait(1)
        end
    end)
    task.spawn(function()
        self.setIdentity(8)
        local Http = game:GetService("HttpService")
        while state.running do
            local entry = settings.queue[1]
            if
                settings.enabled
                and settings.url ~= ""
                and entry
                and entry.url == settings.url
                and os.clock() >= entry.readyAt
            then
                local send = request or http_request or (syn and syn.request) or (http and http.request)
                if type(send) ~= "function" then
                    settings.error = "This executor does not support HTTP requests."
                    table.remove(settings.queue, 1)
                else
                    entry.attempts += 1
                    local ok, response = pcall(function()
                        return send({
                            Url = entry.url,
                            Method = "POST",
                            Headers = { ["Content-Type"] = "application/json" },
                            Body = Http:JSONEncode(entry.payload),
                        })
                    end)
                    local status = ok and type(response) == "table" and tonumber(response.StatusCode) or nil
                    if status and status >= 200 and status < 300 then
                        settings.sent += 1
                        settings.error = nil
                        if settings.queue[1] == entry then
                            table.remove(settings.queue, 1)
                        end
                    elseif status == 429 and entry.attempts < 3 then
                        local delay = 5
                        local parsed, body = pcall(Http.JSONDecode, Http, response.Body or "")
                        if parsed and type(body) == "table" then
                            delay = tonumber(body.retry_after) or delay
                        end
                        entry.readyAt = os.clock() + math.clamp(delay, 1, 300)
                        settings.error = "Discord rate limit reached; waiting before retrying."
                    else
                        settings.error = "Failed to send weather alert"
                            .. (status and (" (HTTP " .. status .. ")") or ".")
                        if settings.queue[1] == entry then
                            table.remove(settings.queue, 1)
                        end
                    end
                end
            end
            task.wait(0.5)
        end
    end)
    tab:AddButton({
        Title = "Webhook Status",
        Callback = function()
            self.window:Notify({
                Title = "Weather Webhook",
                Description = (settings.url == "" and "Enter your Discord Webhook URL to enable delivery.")
                    or settings.error
                    or (
                        tostring(settings.sent)
                        .. " sent; "
                        .. #settings.queue
                        .. " queued. Monitoring "
                        .. (settings.enabled and "enabled." or "disabled.")
                    ),
                Duration = 5,
            })
        end,
    })
end

function Runtime:buildWeatherBoosts()
    local state, tab = self.state, self.tabs.automation
    local m = WeatherBoosts.new()
    state.weatherBoost = m
    local options, weatherOptions, catalog = {}, {}, {}
    for id, info in pairs(self:getBoostCatalog()) do
        if type(info) == "table" and type(info.Boost) == "table" and next(info.Boost) then
            catalog[id] = true
            options[#options + 1] = {
                Title = info.Name or id,
                Value = id,
                Order = tonumber(info.Order) or 999,
                SubOrder = tonumber(info.SubOrder) or 999,
            }
        end
    end
    table.sort(options, function(a, b)
        if a.Order ~= b.Order then
            return a.Order < b.Order
        end
        if a.SubOrder ~= b.SubOrder then
            return a.SubOrder < b.SubOrder
        end
        return a.Title < b.Title
    end)
    for id, info in pairs(self.weatherData.List) do
        weatherOptions[#weatherOptions + 1] =
            { Title = info.Name or id, Value = id, Order = info.Order or 999 }
    end
    table.sort(weatherOptions, function(a, b)
        return a.Order < b.Order
    end)
    tab:AddSection("Weather Boosts")
    tab:AddParagraph({
        Title = "Weather-controlled boosts",
        Description = "Uses one selected boost when needed, pauses it outside selected weather, and resumes its remaining duration when that weather returns. Weather control takes priority over Modes for the same boost. Disabling pauses boosts managed here.",
    })
    state.controls.weatherBoostWeathers = tab:AddDropdown({
        Title = "Boost Weather Selection",
        Multi = true,
        Default = {},
        Options = weatherOptions,
        Placeholder = "Select weather events",
        Callback = function(values)
            m.weathers = {}
            for _, id in ipairs(values) do
                if self.weatherData.List[id] then
                    m.weathers[#m.weathers + 1] = id
                end
            end
        end,
    })
    state.controls.weatherBoostItems = tab:AddDropdown({
        Title = "Weather Boost Selection",
        Multi = true,
        Default = {},
        Options = options,
        Placeholder = "Select boost items",
        Callback = function(values)
            m.boosts = {}
            for _, id in ipairs(values) do
                if catalog[id] then
                    m.boosts[#m.boosts + 1] = id
                end
            end
        end,
    })
    state.controls.weatherBoostEnabled = tab:AddToggle({
        Title = "Auto Use Weather Boosts",
        Default = false,
        Description = "Consumes selected items only during selected weather. Resumes paused duration before using a new item.",
        Callback = function(value)
            m.enabled = value
        end,
    })
    task.spawn(function()
        self.setIdentity(2)
        while state.running and state.weatherBoost == m do
            local ok, err = pcall(function()
                if not self.window.ready or not self.Library.PlayerData then
                    return
                end
                m:step(self.WeatherService.GetActiveList(), self.Library.PlayerData, os.clock(), function(...)
                    self.Library.Remote:Fire(...)
                end)
            end)
            m.error = not ok and tostring(err) or nil
            task.wait(ok and 0.2 or 2)
        end
    end)
end

function Runtime:buildWeatherEquip()
    local state = self.state
    local tab = self.tabs.automation
    local WeatherService = self.WeatherService
    local MultiplierService = self.MultiplierService
    local Library = self.Library
    local choices = { { Title = "Do Nothing", Value = "__none", Order = -1 } }
    for id, info in pairs(self.boostData) do
        if type(info) == "table" and info.EquipBest then
            table.insert(choices, { Title = info.Name or id, Value = id, Order = info.Order or 999 })
        end
    end
    table.sort(choices, function(a, b)
        return a.Order < b.Order
    end)
    local defaults = {
        Lightning = "Energy",
        ["Meteor Shower"] = "Damage",
        Sunset = "Gold",
        ["Lucky Sky"] = "CardLuck",
        Rain = "__none",
        Snow = "__none",
        Toxic = "Energy",
        Aurora = "CardLuck",
        Eclipse = "Drop",
    }
    local weather = { enabled = false, selected = {}, active = nil, applied = nil, error = nil }
    state.weatherEquip = weather
    tab:AddSection("Weather Equip Best")
    state.controls.weatherEquip = tab:AddToggle({
        Title = "Auto Equip Best by Weather",
        Description = "Detects the active weather and equips the best full setup for its configured attribute.",
        Default = false,
        Callback = function(value)
            weather.enabled = value
            weather.applied = nil
        end,
    })
    local weatherList = {}
    for id, info in pairs(self.weatherData.List) do
        table.insert(weatherList, { id = id, name = info.Name or id, order = info.Order or 999 })
    end
    table.sort(weatherList, function(a, b)
        return a.order < b.order
    end)
    for _, entry in ipairs(weatherList) do
        weather.selected[entry.id] = defaults[entry.id] or "__none"
        local valid = false
        for _, choice in ipairs(choices) do
            if choice.Value == weather.selected[entry.id] then
                valid = true
                break
            end
        end
        if not valid then
            weather.selected[entry.id] = "__none"
        end
        state.controls["weather_" .. entry.id] = tab:AddDropdown({
            Title = entry.name,
            Description = "Attribute used by Equip Best while " .. entry.name .. " is active.",
            Multi = false,
            Default = weather.selected[entry.id],
            Options = choices,
            Callback = function(value)
                weather.selected[entry.id] = value
                weather.applied = nil
            end,
        })
    end
    weather.selected.__none = "__none"
    state.controls.weatherOutside = tab:AddDropdown({
        Title = "Outside Weather",
        Description = "Optional Equip Best applied once when every weather event ends.",
        Multi = false,
        Default = "__none",
        Options = choices,
        Callback = function(value)
            weather.selected.__none = value
            weather.applied = nil
        end,
    })
    task.spawn(function()
        self.setIdentity(2)
        while state.running do
            local ok, err = pcall(function()
                local active = WeatherService.GetActiveList()
                local current = active[#active]
                local id = current and current.Id or "__none"
                weather.active = current and current.Id or nil
                if weather.enabled then
                    local aspect = weather.selected[id] or "__none"
                    local signature = id .. ":" .. aspect
                    if signature ~= weather.applied then
                        if aspect ~= "__none" then
                            local boost = MultiplierService:GetBoostName(self.player, aspect)
                            if boost then
                                Library.Remote:Fire("EquipBestSystem", "Apply", boost)
                            end
                        end
                        weather.applied = signature
                    end
                else
                    weather.applied = nil
                end
            end)
            weather.error = not ok and tostring(err) or nil
            task.wait(ok and 1 or 5)
        end
    end)
end

function Runtime:resolveTrialEntry(mode, now)
    local s, G = self.state, self.GamemodeService
    local trial = s.trial
    if mode == "Time Trial" or not trial.enter or G.GetTime() < (trial.skipUntil or 0) then
        return false
    end
    local diff
    for _, selected in ipairs(trial.difficulties or {}) do
        if selected == "Easy" or selected == "Medium" then
            local ok, open = pcall(G.IsOpen, "Time Trial", "The Hallway", selected)
            if ok and open then
                diff = selected
                break
            end
        end
    end
    if not diff then
        return false
    end
    s.target = nil
    s.farmContext = nil
    s.rangeSpot = nil
    trial.pendingDifficulty = diff
    if mode and mode ~= "" then
        s.status = "Leaving " .. tostring(mode) .. " for " .. diff .. " Trial"
        if now >= (trial.nextQuit or 0) then
            trial.nextQuit = now + 2
            trial.nextAction = 0
            self.Library.Remote:Fire("GamemodeSystem", "Quit")
        end
    else
        s.status = "Entering " .. diff .. " Trial"
        if now >= (trial.nextAction or 0) and not self.player:GetAttribute("Teleporting") then
            trial.nextAction = now + 1.5
            self.Library.Remote:Fire("GamemodeSystem", "Enter", "Time Trial", "The Hallway", diff)
        end
    end
    return true
end

function Runtime:startFarm()
    self.setIdentity(8)
    local setIdentity = self.setIdentity
    local CollectionService = self.CollectionService
    local player = self.player
    local Library = self.Library
    local raids = self.raids
    local GamemodeService = self.GamemodeService
    local window = self.window
    local state = self.state
    local raidState = self.raidState
    local trialState = self.trialState
    local fullAuto = state.fullAutoRaid
    local portalState = state.portal
    local ticketEnemies = self.ticketEnemies
    local secretBossList = self.secretBossList
    local toggle = self.toggle
    local enemyCache = {}
    local function refreshPortalRank()
        local ranks = portalState.ranks or {}
        if #ranks == 0 then
            return false
        end
        local items = Library.PlayerData.Items or {}
        for offset = 0, #ranks - 1 do
            local index = (portalState.rankCursor + offset - 1) % #ranks + 1
            local rank = ranks[index]
            local data = (self.portals or {})[rank]
            if data and (tonumber(items[data.OpenItem]) or 0) > 0 then
                portalState.rankCursor = index
                portalState.rank = rank
                return true
            end
        end
        return false
    end
    local enemyConnections = {}
    for _, enemy in ipairs(CollectionService:GetTagged("EnemyServer")) do
        enemyCache[enemy] = true
    end
    enemyConnections[1] = CollectionService:GetInstanceAddedSignal("EnemyServer"):Connect(function(enemy)
        enemyCache[enemy] = true
        if state.rangeSpot then
            state.rangeSpot.untilTime = 0
        end
    end)
    enemyConnections[2] = CollectionService:GetInstanceRemovedSignal("EnemyServer"):Connect(function(enemy)
        enemyCache[enemy] = nil
        if state.rangeSpot then
            state.rangeSpot.untilTime = 0
        end
    end)
    window.Gui.Destroying:Connect(function()
        for _, connection in ipairs(enemyConnections) do
            connection:Disconnect()
        end
        table.clear(enemyCache)
    end)

    local function resolveFarm()
        local mode, sessionId = player:GetAttribute("Mode"), player:GetAttribute("InMode")
        local session = sessionId
            and game.ReplicatedStorage.Server.Gamemode:FindFirstChild(tostring(sessionId))
        local now = os.clock()
        local hasMode = mode ~= nil and tostring(mode) ~= ""
        if hasMode then
            state.lastFarmMode = tostring(mode)
        elseif state.lastFarmMode then
            state.lastFarmMode = nil
            state.resumeFarmJump = true
            state.resumeFarmAt = now + 0.25
            state.rangeSpot = nil
            state.raidEndGameSpot = nil
            state.nextAttackAt = 0
            state.target = nil
            state.farmContext = nil
            state.rangePosition = nil
        end
        if mode == "Portal" then
            portalState.wasInPortal = true
        elseif portalState.wasInPortal then
            portalState.wasInPortal = false
            portalState.nextAction = 0
            state.target = nil
        end
        if trialState.wasInTrial and mode ~= "Time Trial" then
            trialState.wasInTrial = false
            trialState.menuOpen = false
            raidState.menuFor = nil
            raidState.nextAction = 0
            state.target = nil
        end
        if mode == "Time Trial" then
            if not trialState.wasInTrial then
                local diff = session and session:GetAttribute("Diff")
                    or GamemodeService.GetFirstDiff("Time Trial", "The Hallway")
                local entryWindow = GamemodeService.GetWindow("Time Trial", "The Hallway", diff)
                trialState.skipUntil = math.max(
                    trialState.skipUntil,
                    entryWindow and entryWindow.ClosesAt or (GamemodeService.GetTime() + 60)
                )
                trialState.wasInTrial = true
            end
        end
        local worldBossHandled, worldBossContext = self:resolveWorldBossFarm(mode, now)
        if worldBossHandled then
            return worldBossContext
        end
        local ghoulHandled, ghoulContext = self:resolveGhoulFarm(mode, now)
        if ghoulHandled then
            return ghoulContext
        end
        if self:resolveTrialEntry(mode, now) then
            return nil
        end
        local invasionHandled, invasionContext = self:resolveInvasion(mode, session, sessionId, now)
        if invasionHandled then
            return invasionContext
        end
        local defenseHandled, defenseContext = self:resolveDefense(mode, session, sessionId, now)
        if defenseHandled then
            return defenseContext
        end
        local towerHandled, towerContext = self:resolveMagicTower(mode, session, sessionId, now)
        if towerHandled then
            return towerContext
        end
        if mode then
            if mode == "Portal" then
                if
                    not session
                    or (
                        not state.rooms.Portal.join
                        and not table.find(portalState.ranks, session:GetAttribute("MapId"))
                    )
                then
                    return nil
                end
                local portalStatus = tostring(session:GetAttribute("Status") or "")
                if
                    portalStatus == "Completed"
                    or portalStatus == "Complete"
                    or portalStatus == "Finished"
                    or portalStatus == "Ended"
                    or portalStatus == "Closed"
                then
                    state.target = nil
                    portalState.startAt = 0
                    portalState.nextAction = now + 3
                    Library.Remote:Fire("GamemodeSystem", "Quit")
                    return nil
                end
                local stage = tonumber(session:GetAttribute("Stage")) or 0
                if portalState.leave and stage >= portalState.wave then
                    if now >= portalState.nextAction then
                        portalState.nextAction = now + 3
                        Library.Remote:Fire("GamemodeSystem", "Quit")
                    end
                    return nil
                end
                if session:GetAttribute("Status") == "Opened" then
                    if
                        portalState.open
                        and session:GetAttribute("HostId") == player.UserId
                        and now >= portalState.startAt
                        and self:roomReady("Portal", session)
                    then
                        portalState.startAt = now + 1
                        Library.Remote:Fire("GamemodeSystem", "Start", "Portal", player.UserId)
                    end
                    return nil
                end
                if not portalState.farm then
                    return nil
                end
                local folder = workspace._ENEMIES.Server:FindFirstChild("Gamemode")
                local scope = folder and folder:FindFirstChild(tostring(sessionId))
                return scope and { key = "portal:" .. tostring(sessionId), scope = scope } or nil
            end
            if mode == "Time Trial" then
                if not session or session:GetAttribute("MapId") ~= "The Hallway" then
                    return nil
                end
                local trialStatus = tostring(session:GetAttribute("Status") or "")
                if
                    trialStatus == "Completed"
                    or trialStatus == "Complete"
                    or trialStatus == "Finished"
                    or trialStatus == "Ended"
                    or trialStatus == "Closed"
                then
                    state.target = nil
                    trialState.nextAction = now + 3
                    Library.Remote:Fire("GamemodeSystem", "Quit")
                    return nil
                end
                local stage = tonumber(session:GetAttribute("Stage")) or 0
                local leaveRule = trialState.leaveByDifficulty[session:GetAttribute("Diff")]
                if leaveRule and leaveRule.enabled and stage >= leaveRule.wave then
                    if now >= trialState.nextAction then
                        trialState.nextAction = now + 3
                        local entryWindow = GamemodeService.GetWindow(
                            "Time Trial",
                            "The Hallway",
                            session:GetAttribute("Diff") or "Easy"
                        )
                        trialState.skipUntil = entryWindow and entryWindow.ClosesAt
                            or (GamemodeService.GetTime() + 60)
                        Library.Remote:Fire("GamemodeSystem", "Quit")
                    end
                    return nil
                end
                if not trialState.farm then
                    return nil
                end
                local folder = workspace._ENEMIES.Server:FindFirstChild("Gamemode")
                local scope = folder and folder:FindFirstChild(tostring(sessionId))
                return scope and { key = "trial:" .. tostring(sessionId), scope = scope } or nil
            end
            if
                mode ~= "Raid"
                or not session
                or (
                    not fullAuto.enabled
                    and not state.rooms.Raid.join
                    and session:GetAttribute("MapId") ~= raidState.id
                )
            then
                return nil
            end
            local raidStatus = tostring(session:GetAttribute("Status") or "")
            if
                raidStatus == "Completed"
                or raidStatus == "Complete"
                or raidStatus == "Finished"
                or raidStatus == "Ended"
                or raidStatus == "Closed"
            then
                state.target = nil
                raidState.nextAction = now + 3
                Library.Remote:Fire("GamemodeSystem", "Quit")
                return nil
            end
            local stage = tonumber(session:GetAttribute("Stage")) or 0
            local leaveAt = fullAuto.enabled and 100 or raidState.wave
            if (raidState.leave or fullAuto.enabled) and stage >= leaveAt then
                if now >= raidState.nextAction then
                    raidState.nextAction = now + 3
                    Library.Remote:Fire("GamemodeSystem", "Quit")
                end
                return nil
            end
            if session:GetAttribute("Status") == "Opened" then
                if
                    (raidState.enter or fullAuto.enabled)
                    and session:GetAttribute("HostId") == player.UserId
                    and now >= (raidState.startAt or 0)
                    and self:roomReady("Raid", session)
                then
                    raidState.startAt = now + 1
                    Library.Remote:Fire("GamemodeSystem", "Start", "Raid", player.UserId)
                end
                return nil
            end
            if not raidState.farm and not fullAuto.enabled then
                return nil
            end
            local folder = workspace._ENEMIES.Server:FindFirstChild("Gamemode")
            local scope = folder and folder:FindFirstChild(tostring(sessionId))
            return scope and { key = "raid:" .. tostring(sessionId), scope = scope } or nil
        end
        if self:joinPublicRoom(now) then
            return nil
        end
        if portalState.open and portalState.rank and not state.rooms.Portal.join then
            refreshPortalRank()
            local portal = (self.portals or {})[portalState.rank]
            if not portal then
                return nil
            end
            local tickets = tonumber(Library.PlayerData.Items[portal.OpenItem]) or 0
            if tickets <= 0 then
                return nil
            end
            if now >= portalState.nextAction then
                portalState.nextAction = now + 1.5
                local diff = GamemodeService.GetFirstDiff("Portal", portalState.rank)
                Library.Remote:Fire("GamemodeSystem", "Create", "Portal", portalState.rank, diff, false)
            end
            return nil
        end
        if fullAuto.enabled and not state.rooms.Raid.join then
            local count = #raids
            local ids = {}
            for id in pairs(raids) do
                ids[#ids + 1] = id
            end
            table.sort(ids, function(a, b)
                return (raids[a].Order or 999) < (raids[b].Order or 999)
            end)
            if fullAuto.phase == "raids" then
                for offset = 0, #ids - 1 do
                    local index = (fullAuto.cursor + offset - 1) % #ids + 1
                    local id = ids[index]
                    local raid = raids[id]
                    if
                        Library.PlayerData.UnlockedMap[raid.RequiredMap]
                        and (tonumber(Library.PlayerData.Items[raid.RequiredItem]) or 0) > 0
                    then
                        fullAuto.cursor = index % #ids + 1
                        fullAuto.activeId = id
                        raidState.id = id
                        if now >= raidState.nextAction then
                            raidState.nextAction = now + 1.5
                            local diff = GamemodeService.GetFirstDiff("Raid", id)
                            Library.Remote:Fire("GamemodeSystem", "Create", "Raid", id, diff, false)
                        end
                        state.status = "Full Auto Raid: " .. tostring(raid.Name or id)
                        return nil
                    end
                end
                fullAuto.phase = "tickets"
                fullAuto.cursor = 1
            end
            if fullAuto.phase == "tickets" then
                for offset = 0, #ids - 1 do
                    local index = (fullAuto.cursor + offset - 1) % #ids + 1
                    local id = ids[index]
                    local raid = raids[id]
                    if
                        Library.PlayerData.UnlockedMap[raid.RequiredMap]
                        and (tonumber(Library.PlayerData.Items[raid.RequiredItem]) or 0)
                            < fullAuto.targetTickets
                    then
                        fullAuto.cursor = index
                        state.status = "Farming "
                            .. tostring(raid.RequiredItem)
                            .. " to "
                            .. fullAuto.targetTickets
                        return {
                            key = "full-ticket:" .. id,
                            world = raid.RequiredMap,
                            selected = ticketEnemies[id],
                        }
                    end
                end
                fullAuto.phase = "raids"
                fullAuto.cursor = 1
                fullAuto.activeId = nil
            end
            return nil
        end
        if raidState.enter and not state.rooms.Raid.join then
            local raid = raids[raidState.id]
            if not raid or not Library.PlayerData.UnlockedMap[raid.RequiredMap] then
                return nil
            end
            local tickets = tonumber(Library.PlayerData.Items[raid.RequiredItem]) or 0
            if tickets <= 0 then
                raidState.ticketBatchReady = false
            end
            if raidState.waitTickets and tickets >= raidState.ticketAmount then
                raidState.ticketBatchReady = true
            end
            if tickets <= 0 or (raidState.waitTickets and not raidState.ticketBatchReady) then
                raidState.menuFor = nil
                state.status = "Farming "
                    .. tostring(raid.RequiredItem)
                    .. ": "
                    .. tickets
                    .. "/"
                    .. (raidState.waitTickets and raidState.ticketAmount or 1)
                return {
                    key = "ticket:" .. raidState.id,
                    world = raid.RequiredMap,
                    selected = ticketEnemies[raidState.id],
                }
            end
            if now >= raidState.nextAction then
                raidState.nextAction = now + 1.5
                local diff = GamemodeService.GetFirstDiff("Raid", raidState.id)
                Library.Remote:Fire("GamemodeSystem", "Create", "Raid", raidState.id, diff, false)
            end
            return nil
        end
        if state.secretBosses.enabled then
            local secret = state.secretBosses
            local count = #secretBossList
            if count == 0 then
                return nil
            end

            local function alive(enemy)
                return enemy
                    and enemy.Parent
                    and enemy:IsA("BasePart")
                    and not enemy:GetAttribute("Dead")
                    and not enemy:GetAttribute("Shield")
                    and (tonumber(enemy:GetAttribute("HP")) or 0) > 0
            end
            local function matchesBoss(enemy, boss)
                if not alive(enemy) then
                    return false
                end
                if boss.type == "GlobalBoss" then
                    return enemy:GetAttribute("Type") == "GlobalBoss"
                        and enemy:GetAttribute("Id") == boss.id
                end
                return enemy:GetAttribute("Id") == boss.id
                    and (not boss.type or enemy:GetAttribute("Type") == boss.type)
                    and enemy:GetAttribute("Map") == boss.world
            end
            local function findBossInGlobalFolder(boss)
                local enemies = workspace:FindFirstChild("_ENEMIES")
                local server = enemies and enemies:FindFirstChild("Server")
                local globalBosses = server and server:FindFirstChild("GlobalBoss")
                if boss.type ~= "GlobalBoss" or not globalBosses then
                    return nil
                end
                for _, enemy in ipairs(globalBosses:QueryDescendants("BasePart[$Id]")) do
                    if matchesBoss(enemy, boss) then
                        return enemy
                    end
                end
                return nil
            end

            if not alive(secret.current) then
                secret.current = nil
                local scan = secret.scan
                if not scan then
                    for offset = 0, count - 1 do
                        local index = (secret.cursor + offset - 1) % count + 1
                        local boss = secretBossList[index]
                        if Library.PlayerData.UnlockedMap[boss.world] then
                            scan = { index = index, boss = boss, deadline = now + 20, nextTravel = 0 }
                            secret.scan = scan
                            break
                        end
                    end
                end
                if not scan then
                    state.status = "No selected Secret boss world is unlocked"
                    return nil
                end

                local boss = scan.boss
                if Library.PlayerData.CurrentMap ~= boss.world or player:GetAttribute("Teleporting") then
                    state.status = "Loading Secret boss world: " .. boss.world
                    if now >= scan.deadline then
                        secret.cursor = scan.index % count + 1
                        secret.scan = nil
                        return nil
                    end
                    if not player:GetAttribute("Teleporting") and now >= scan.nextTravel then
                        scan.nextTravel = now + 5
                        Library.Remote:Fire("TeleportSystem", "To", boss.world)
                    end
                    return nil
                end

                if not scan.arrived then
                    scan.arrived = true
                    scan.deadline = now + 8
                end
                for enemy in pairs(enemyCache) do
                    if matchesBoss(enemy, boss) then
                        secret.current = enemy
                        secret.cursor = scan.index % count + 1
                        secret.scan = nil
                        break
                    end
                end
                if not secret.current and boss.type == "GlobalBoss" then
                    secret.current = findBossInGlobalFolder(boss)
                    if secret.current then
                        enemyCache[secret.current] = true
                        secret.cursor = scan.index % count + 1
                        secret.scan = nil
                    end
                end
                if not secret.current then
                    state.status = "Waiting for Secret boss: " .. boss.id
                    if now >= scan.deadline then
                        secret.cursor = scan.index % count + 1
                        secret.scan = nil
                    end
                    return nil
                end
            end

            local target = secret.current
            return {
                key = "secret:" .. target.Name,
                world = target:GetAttribute("Map"),
                selected = { [target:GetAttribute("Id")] = true },
                secretTarget = target,
            }
        end
        if state.enabled and Library.PlayerData.UnlockedMap[state.world] then
            return {
                key = "normal:" .. tostring(state.world),
                world = state.world,
                selected = state.selected,
                priorityEnemy = state.priorityEnemy,
            }
        end
    end

    local function valid(enemy)
        local context = state.farmContext
        if not context or not enemy or not enemy.Parent or not enemy:IsA("BasePart") then
            return false
        end
        if
            enemy:GetAttribute("Dead")
            or enemy:GetAttribute("Shield")
            or (tonumber(enemy:GetAttribute("HP")) or 0) <= 0
        then
            return false
        end
        if context.scope then
            return enemy:IsDescendantOf(context.scope)
        end
        if context.secretTarget then
            return enemy == context.secretTarget
        end
        return enemy:GetAttribute("Type") == "Normal"
            and enemy:GetAttribute("Map") == context.world
            and context.selected
            and context.selected[enemy:GetAttribute("Id")] == true
    end
    local candidates = {}
    local function step()
        local shardCollector = state.hogyokuCollector
        if shardCollector and shardCollector.enabled and shardCollector.collecting then
            state.target = nil
            state.farmContext = nil
            state.rangePosition = nil
            state.rangeSpot = nil
            state.raidEndGameSpot = nil
            state.nextAttackAt = 0
            state.status = shardCollector.leavingMode and "Leaving gamemode for Hogyoku Shard"
                or "Collecting Hogyoku Shard"
            return
        end
        local worldBossActive = self:updateWorldBossPriority(os.clock(), enemyCache)
        local ghoulActive = not worldBossActive and self:updateGhoulPriority(os.clock(), enemyCache)
        local collector = state.fragmentCollector
        if
            not worldBossActive
            and not ghoulActive
            and collector
            and collector.enabled
            and collector.collecting
        then
            state.target = nil
            state.farmContext = nil
            state.rangePosition = nil
            state.status = collector.leavingMode and "Leaving gamemode for Commandment Fragment"
                or "Collecting Commandment Fragment"
            return
        end
        local context = resolveFarm()
        if not context then
            state.target = nil
            state.farmContext = nil
            return
        end
        if not state.farmContext or state.farmContext.key ~= context.key then
            state.target = nil
        end
        state.farmContext = context
        local char = player.Character
        local root = char and char:FindFirstChild("HumanoidRootPart")
        local humanoid = char and char:FindFirstChildOfClass("Humanoid")
        if not root or not humanoid or humanoid.Health <= 0 then
            state.status = "Waiting for respawn"
            state.target = nil
            return
        end
        if state.resumeFarmJump then
            if root.Anchored then
                state.status = "Waiting for teleport release"
                return
            end
            if os.clock() >= (state.resumeFarmAt or 0) then
                state.resumeFarmJump = false
                state.resumeMotionUntil = os.clock() + 0.8
                humanoid.Sit = false
                humanoid.Jump = true
                humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
                return
            else
                state.status = "Recovering after gamemode"
                return
            end
        end
        if os.clock() < (state.resumeMotionUntil or 0) then
            return
        end
        local needsTarget = not valid(state.target)
        local needsBatch = state.farmMode == "EndGame"
            and not player:GetAttribute("UsingSkill")
            and os.clock() >= (state.nextAttackAt or 0)
        if needsTarget or needsBatch then
            table.clear(candidates)
            for enemy in pairs(enemyCache) do
                if valid(enemy) then
                    candidates[enemy] = true
                end
            end
        end
        if needsTarget then
            local old = state.target
            if
                old
                and old.Parent
                and (old:GetAttribute("Dead") or (tonumber(old:GetAttribute("HP")) or 1) <= 0)
            then
                state.defeated += 1
            end
            state.target = nil
            local distance = math.huge
            local bestPriority = math.huge
            for enemy in pairs(candidates) do
                do
                    local delta = enemy.Position - root.Position
                    local d = delta:Dot(delta)
                    local priority = context.priorityEnemy
                            and enemy:GetAttribute("Id") == context.priorityEnemy
                            and 0
                        or 1
                    if priority < bestPriority or (priority == bestPriority and d < distance) then
                        state.target = enemy
                        distance = d
                        bestPriority = priority
                    end
                end
            end
            state.targetSince = os.clock()
            state.lastHP = state.target and state.target:GetAttribute("HP")
            state.lastProgress = os.clock()
        end
        local target = state.target
        if not target then
            local idlePosition = self:rangeFarmPosition(context, nil, candidates)
            if idlePosition and (root.Position - idlePosition).Magnitude > 2 then
                root.CFrame = CFrame.new(idlePosition)
                root.AssemblyLinearVelocity = Vector3.zero
            end
            state.status = "Waiting for selected NPCs to respawn"
            return
        end
        local rangePosition, rangeRadius = self:rangeFarmPosition(context, target, enemyCache)
        state.rangePosition = rangePosition
        local destination = rangePosition or target.Position + Vector3.new(0, 2, 4)
        if (root.Position - destination).Magnitude > 2 then
            local facing = Vector3.new(target.Position.X, destination.Y, target.Position.Z)
            root.CFrame = (destination - facing).Magnitude > 0.01 and CFrame.lookAt(destination, facing)
                or CFrame.new(destination)
            root.AssemblyLinearVelocity = Vector3.zero
        end
        if not state.running or not valid(target) then
            return
        end
        local now = os.clock()
        if not player:GetAttribute("UsingSkill") and now >= (state.nextAttackAt or 0) then
            local previous = state.nextAttackAt or 0
            -- Preserve 20/s pacing without accumulating a frame of delay per attack.
            state.nextAttackAt = previous > 0 and now - previous < 0.05 and previous + 0.05 or now + 0.05
            local targets = { target.Name }
            if rangePosition then
                targets = {}
                for enemy in pairs(candidates) do
                    do
                        local d = enemy.Position - root.Position
                        if
                            d.X * d.X + d.Z * d.Z <= rangeRadius * rangeRadius
                            and math.abs(d.Y) <= rangeRadius
                        then
                            targets[#targets + 1] = enemy.Name
                        end
                    end
                end
            end
            state.rangeTargetCount = #targets
            if #targets > 0 then
                Library.Remote:Fire("ClickSystem", "Execute", targets)
                state.attacks += 1
            end
        end
        local hp = target:GetAttribute("HP")
        if hp ~= state.lastHP then
            state.lastProgress = os.clock()
            state.lastHP = hp
        end
        state.status = "Attacking: "
            .. tostring(target:GetAttribute("Name") or target:GetAttribute("Id"))
            .. " | HP: "
            .. tostring(hp)
        if os.clock() - state.lastProgress > 10 then
            state.status = "No damage confirmed: " .. tostring(target:GetAttribute("Name"))
            if
                not player:GetAttribute("Mode")
                and not root.Anchored
                and not player:GetAttribute("UsingSkill")
                and os.clock() >= (state.nextRecoveryAt or 0)
            then
                state.nextRecoveryAt = os.clock() + 15
                state.target = nil
                state.rangeSpot = nil
                state.resumeFarmJump = true
                state.resumeFarmAt = os.clock()
            end
        end
    end
    if self.replaceFarmStep then
        self.replaceFarmStep(step)
        return
    end
    task.spawn(function()
        state.loopStarted = true
        setIdentity(2)
        while state.running do
            state.lastTick = os.clock()
            local ok, err = pcall(step)
            if not ok then
                state.target = nil
                state.farmContext = nil
                state.rangeSpot = nil
                state.error = tostring(err)
                state.status = "Error: " .. tostring(err)
                task.wait(1)
            else
                state.error = nil
            end
            if state.target or state.farmContext then
                task.wait()
            else
                task.wait(0.1)
            end
        end
    end)
    task.spawn(function()
        while state.running do
            if toggle:Get() ~= state.enabled then
                toggle:Set(state.enabled, true)
            end
            if state.controls.enterRaid:Get() ~= raidState.enter then
                state.controls.enterRaid:Set(raidState.enter, true)
            end
            if state.controls.farmRaid:Get() ~= raidState.farm then
                state.controls.farmRaid:Set(raidState.farm, true)
            end
            if state.controls.leaveRaid:Get() ~= raidState.leave then
                state.controls.leaveRaid:Set(raidState.leave, true)
            end
            if state.controls.openPortal:Get() ~= portalState.open then
                state.controls.openPortal:Set(portalState.open, true)
            end
            if state.controls.farmPortal:Get() ~= portalState.farm then
                state.controls.farmPortal:Set(portalState.farm, true)
            end
            if state.controls.leavePortal:Get() ~= portalState.leave then
                state.controls.leavePortal:Set(portalState.leave, true)
            end
            if state.controls.enterTrial:Get() ~= trialState.enter then
                state.controls.enterTrial:Set(trialState.enter, true)
            end
            if state.controls.trialDifficulty then
                local current = state.controls.trialDifficulty:Get()
                local expected = trialState.difficulties or {}
                if type(current) ~= "table" or #current ~= #expected then
                    state.controls.trialDifficulty:Set(expected, true)
                end
            end
            if state.controls.farmTrial:Get() ~= trialState.farm then
                state.controls.farmTrial:Set(trialState.farm, true)
            end

            task.wait(0.5)
        end
    end)
end

function Runtime:buildGacha()
    local Players = self.Players
    local player = self.player
    local Library = self.Library
    local AutoService = self.AutoService
    local window = self.window
    local state = self.state
    do
        local S = self.state
        if S.scrollControl then
            return
        end
        local identity = setthreadidentity or setidentity
        identity(2)
        local L = self.Library
        local configs = L:GetData("GachaConfig")
        local amuletData = L:GetData("AmuletData")
        local petData = L:GetData("PetData")
        local warriorData = L:GetData("WarriorData")
        local weaponData = L:GetData("WeaponData")
        local upgrades = L:GetData("UpgradeData")
        local GS = L:GetService("GachaService")
        local AS = L:GetService("AutoService")
        local US = L:GetService("UpgradeService")
        local MS = L:GetService("MultiplierService")
        local player = game.Players.LocalPlayer
        identity(8)
        local window = S.window
        local tab = self.tabs.gacha
        local C = {
            gachas = {},
            fighters = {},
            gachaOn = false,
            fighterOn = false,
            shadowOn = false,
            upgradeOn = false,
            priorities = {},
            cursor = 1,
            owned = {},
            retry = {},
            controls = {},
        }
        S.scrollControl = C
        local choices, fighterChoices, lookup = {}, {}, {}
        for id, config in pairs(configs) do
            for kind, info in pairs(config.Types) do
                local key = id .. "/" .. kind
                lookup[key] = { id = id, kind = kind, info = info, config = config }
                local option = {
                    Title = (config.Name or id) .. (kind == "Default" and "" or " - " .. (info.Name or kind)),
                    Value = key,
                }
                table.insert(choices, option)
                if id == "Pet" then table.insert(fighterChoices, option) end
            end
        end
        C.lookup = lookup
        local function sortOptions(options)
            table.sort(options, function(a, b)
                return a.Title < b.Title
            end)
        end
        sortOptions(choices)
        sortOptions(fighterChoices)
        local function limited(field, control, values)
            local selected = {}
            local limit = math.max(1, math.floor(tonumber(MS.SimulSpin(player)) or 1))
            for _, key in ipairs(values) do
                if lookup[key] and not table.find(selected, key) and #selected < limit then
                    table.insert(selected, key)
                end
            end
            C[field] = selected
            if #values > limit then
                if C.controls[control] then
                    C.controls[control]:Set(selected, true)
                end
                window:Notify({
                    Title = "Selection limit",
                    Description = "Select up to " .. limit .. " per list. All spins share the game's slot limit.",
                    Duration = 4,
                })
            end
        end
        tab:AddSection("Gacha")
        C.controls.gachas = tab:AddDropdown({
            Title = "Select Gacha",
            Multi = true,
            Default = {},
            Options = choices,
            Callback = function(v)
                limited("gachas", "gachas", v)
            end,
        })
        C.controls.gachaOn = tab:AddToggle({
            Title = "Auto Spin Gacha",
            Default = false,
            Description = "Uses available tokens and native spin slots",
            Callback = function(v)
                C.gachaOn = v
            end,
        })
        tab:AddSection("Amulet Building")
        local amuletOptions = {}
        for uid, item in pairs(L.PlayerData.Amulets or {}) do
            if type(item) == "table" then
                table.insert(amuletOptions, {
                    Title = (amuletData[item.Id] and amuletData[item.Id].Name or item.Id or "Amulet")
                        .. " - "
                        .. tostring(uid),
                    Value = uid,
                })
            end
        end
        C.controls.amulet = tab:AddDropdown({
            Title = "Amulet Building Target",
            Flag = "gacha.Spin.Gacha.Amulet Building Target",
            Description = "Required only for Amulet Building; rerolls the selected amulet",
            Multi = false,
            Options = amuletOptions,
            Callback = function(v)
                C.amulet = v
            end,
        })
        tab:AddSection("Hero Passives")
        local function heroOptions()
            local result = {}
            for uid, item in pairs(L.PlayerData.Pets or {}) do
                if type(item) == "table" then
                    local info = petData[item.Id]
                    result[#result + 1] = {
                        Title = (info and info.Name or item.Id or "Hero")
                            .. (item.Equipped and " [Equipped]" or "")
                            .. " - "
                            .. tostring(uid):sub(1, 8),
                        Value = uid,
                    }
                end
            end
            sortOptions(result)
            return result
        end
        C.controls.hero = tab:AddDropdown({
            Title = "Hero Passive Target",
            Flag = "gacha.Spin.Gacha.Hero Passive Target",
            Description = "Character to reroll when Hero Passives is selected in Select Gacha. Uses the stop targets configured in the game's Manage menu.",
            Multi = false,
            Options = heroOptions(),
            Callback = function(v)
                C.hero = v
            end,
        })
        C.heroOptions = heroOptions
        tab:AddSection("Shadow Passives")
        local function shadowOptions()
            local options = {}
            for uid, item in pairs(L.PlayerData.Warriors or {}) do
                local info = warriorData[item.Id]
                if info and info.Type == "Shadow" then
                    options[#options + 1] =
                        { Title = info.Name .. " - " .. tostring(uid):sub(1, 8), Value = uid }
                end
            end
            sortOptions(options)
            return options
        end
        C.controls.shadow = tab:AddDropdown({
            Title = "Shadow Passive Target",
            Flag = "gacha.Spin.Gacha.Shadow Passive Target",
            Description = "Select the Shadow to roll. Stop targets come from the game's Manage menu.",
            Multi = false,
            Options = shadowOptions(),
            Callback = function(v)
                C.shadow = v
            end,
        })
        C.controls.shadowOn = tab:AddToggle({
            Title = "Auto Roll Shadow Passives",
            Flag = "gacha.Spin.Gacha.Auto Roll Shadow Passives",
            Default = false,
            Description = "Uses Shadow Passive Coins and available Spin Manager slots.",
            Callback = function(v)
                C.shadowOn = v
            end,
        })
        S.controls.shadowTarget = C.controls.shadow
        S.controls.shadowRoll = C.controls.shadowOn
        tab:AddButton({
            Title = "Refresh Shadow List",
            Callback = function()
                C.controls.shadow:Reload(shadowOptions())
                if C.shadow and not L.PlayerData.Warriors[C.shadow] then
                    C.controls.shadow:Set(nil)
                end
            end,
        })
        tab:AddSection("Titan Passives")
        local function titanOptions()
            local options = {}
            for uid, item in pairs(L.PlayerData.Warriors or {}) do
                local info = type(item) == "table" and warriorData[item.Id]
                if info and info.Type == "Titan" then
                    options[#options + 1] = { Title = (info.Name or item.Id) .. " - " .. tostring(uid):sub(1, 8), Value = uid }
                end
            end
            sortOptions(options)
            return options
        end
        C.controls.titan = tab:AddDropdown({
            Title = "Titan Passive Target",
            Flag = "gacha.Spin.Gacha.Titan Passive Target",
            Description = "Select a Titan, then select Titan Passives in Select Gacha. Uses the stop targets from Manage.",
            Multi = false,
            Options = titanOptions(),
            Callback = function(value) C.titan = value end,
        })
        tab:AddSection("Weapon Passives")
        local function weaponOptions()
            local options = {}
            for uid, item in pairs(L.PlayerData.Weapons or {}) do
                if type(item) == "table" and weaponData[item.Id] then
                    options[#options + 1] = {
                        Title = (weaponData[item.Id].Name or item.Id) .. " - " .. tostring(uid):sub(1, 8),
                        Value = uid,
                    }
                end
            end
            sortOptions(options)
            return options
        end
        C.controls.weapon = tab:AddDropdown({
            Title = "Weapon Passive Target",
            Flag = "gacha.Spin.Gacha.Weapon Passive Target",
            Description = "Select the weapon to reroll. Stop targets come from the game Manage menu.",
            Multi = false,
            Options = weaponOptions(),
            Callback = function(v)
                C.weapon = v
            end,
        })
        C.controls.weaponOn = tab:AddToggle({
            Title = "Auto Roll Weapon Passives",
            Flag = "gacha.Spin.Gacha.Auto Roll Weapon Passives",
            Description = "Uses Weapon Passive Coins and native spin slots.",
            Default = false,
            Callback = function(v)
                C.weaponOn = v
            end,
        })
        tab:AddButton({
            Title = "Refresh Gacha Targets",
            Callback = function()
                C.controls.titan:Reload(titanOptions())
                C.controls.hero:Reload(heroOptions())
                C.controls.shadow:Reload(shadowOptions())
                C.controls.weapon:Reload(weaponOptions())
                local options = {}
                for uid, item in pairs(L.PlayerData.Amulets or {}) do
                    if type(item) == "table" then
                        options[#options + 1] = {
                            Title = (amuletData[item.Id] and amuletData[item.Id].Name or item.Id or "Amulet")
                                .. " - "
                                .. tostring(uid),
                            Value = uid,
                        }
                    end
                end
                sortOptions(options)
                C.controls.amulet:Reload(options)
                for _, field in ipairs({ "hero", "shadow", "weapon", "amulet", "titan" }) do
                    C[field] = C.controls[field]:Get()
                end
            end,
        })
        local function selectedTarget(config)
            local field = ({ Pet = "hero", Amulet = "amulet", Warrior = "shadow", Weapon = "weapon" })[config.SelectGacha]
            local warriorType = config == configs["Titan Passive"] and "Titan" or "Shadow"
            if config.SelectGacha == "Warrior" and warriorType == "Titan" then field = "titan" end
            local inventory = ({ Pet = "Pets", Amulet = "Amulets", Warrior = "Warriors", Weapon = "Weapons" })[config.SelectGacha]
            local uid = field and C[field]
            local item = inventory and (L.PlayerData[inventory] or {})[uid]
            if not item then
                return nil
            end
            if
                config.SelectGacha == "Warrior"
                and (not warriorData[item.Id] or warriorData[item.Id].Type ~= warriorType)
            then
                return nil
            end
            return uid
        end
        tab:AddSection("Fighters")
        C.controls.fighters = tab:AddDropdown({
            Title = "Select Fighters",
            Multi = true,
            Default = {},
            Options = fighterChoices,
            Callback = function(v)
                limited("fighters", "fighters", v)
            end,
        })
        C.controls.fighterOn = tab:AddToggle({
            Title = "Auto Spin Fighters",
            Default = false,
            Description = "Uses Gold and shares spin slots with gachas",
            Callback = function(v)
                C.fighterOn = v
            end,
        })
        tab:AddSection("Upgrades")
        local systems = {}
        for id, d in pairs(upgrades) do
            if not d.Stages then
                table.insert(systems, { Title = d.Name or id, Value = id })
            end
        end
        sortOptions(systems)
        C.controls.system = tab:AddDropdown({
            Title = "Select Upgrade",
            Multi = false,
            Options = systems,
            Callback = function(id)
                C.system = id
                C.cursor = 1
                C.pending = nil
                C.priorities = {}
                local opts = {}
                for _, key in ipairs(AS.GetUpgradeTargets(id)) do
                    table.insert(opts, {
                        Title = (
                            id == "Offline Upgrades" and key == "MaxTime" and "Hibernation - AFK Max Time"
                            or AS.GetTargetLabel(id, key)
                        )
                            .. " ("
                            .. key
                            .. ")",
                        Value = key,
                    })
                end
                if C.controls.priorities then
                    C.controls.priorities:Reload(opts)
                    C.controls.priorities:Set({}, true)
                end
            end,
        })
        C.controls.priorities = tab:AddDropdown({
            Title = "Upgrade Priorities",
            Description = "One purchase per selected priority, in rotation; waits for its cost",
            Multi = true,
            Default = {},
            Options = {},
            Callback = function(v)
                C.priorities = v
                C.cursor = 1
                C.pending = nil
            end,
        })
        C.controls.upgradeOn = tab:AddToggle({
            Title = "Auto Upgrade",
            Default = false,
            Callback = function(v)
                C.upgradeOn = v
            end,
        })
        tab:AddSection("Craft")
        local crafts = { { Title = "Commandment Totem", Value = "Commandment Totem" } }
        for id, info in pairs(upgrades) do
            if info.Stages and id ~= "Commandment Totem" then
                crafts[#crafts + 1] = { Title = info.Name or id, Value = id }
            end
        end
        sortOptions(crafts)
        C.craft = "Commandment Totem"
        C.craftOn = false
        C.controls.craft = tab:AddDropdown({
            Title = "Select Craft",
            Multi = false,
            Default = C.craft,
            Options = crafts,
            Callback = function(v)
                C.craft = v
            end,
        })
        C.controls.craftOn = tab:AddToggle({
            Title = "Auto Craft",
            Description = "Advances the selected totem using its materials. Commandment Totem uses Commandment Fragments. Stops at the final stage.",
            Default = false,
            Callback = function(v)
                C.craftOn = v
            end,
        })
        local function craftStep()
            if not C.craftOn or not C.craft or os.clock() < (C.craftRetry or 0) then
                return
            end
            local config = upgrades[C.craft]
            if not config or not config.Stages or not AS.CanUseUpgrade(L.PlayerData, C.craft) then
                return
            end
            local level = L.PlayerData.Upgrades[C.craft .. "_Stage"] or 0
            local nextStage = config.Stages[level + 1]
            if not nextStage then
                return
            end
            for _, item in ipairs(nextStage.Items or {}) do
                if (L.PlayerData.Items[item.Id] or 0) < item.Amount then
                    return
                end
            end
            C.craftRetry = os.clock() + 3
            L.Remote:Fire("UpgradeSystem", "Buy", C.craft, "Stage")
        end
        local function spinStep()
            local desired = {}
            for _, group in ipairs({
                { C.gachaOn, C.gachas },
                { C.fighterOn, C.fighters },
            }) do
                if group[1] then
                    for _, key in ipairs(group[2]) do
                        local d = lookup[key]
                        if d then
                            desired[d.id .. d.kind] = d
                        end
                    end
                end
            end
            local active = L.PlayerData.SpinManager or {}
            if C.shadowOn then
                local d = lookup["Shadow Passive/Default"]
                if d then
                    desired[d.id .. d.kind] = d
                end
            end
            if C.weaponOn then
                local d = lookup["Weapon Passive/Default"]
                if d then
                    desired[d.id .. d.kind] = d
                end
            end
            for key, d in pairs(desired) do
                if d.config.SelectGacha and not selectedTarget(d.config) then
                    desired[key] = nil
                end
            end
            local shadow = L.PlayerData.Warriors and L.PlayerData.Warriors[C.shadow]
            if not shadow or not warriorData[shadow.Id] or warriorData[shadow.Id].Type ~= "Shadow" then
                desired["Shadow PassiveDefault"] = nil
            end
            for key, d in pairs(desired) do
                if active[key] then
                    C.owned[key] = true
                    local target = selectedTarget(d.config)
                    if target and active[key].Selected ~= target then
                        if os.clock() >= (C.retry[key] or 0) then
                            C.retry[key] = os.clock() + 2
                            L.Remote:Fire("SpinManagerSystem", "Remove", key)
                        end
                        return
                    end
                end
            end
            for key in pairs(C.owned) do
                if not desired[key] then
                    if active[key] then
                        L.Remote:Fire("SpinManagerSystem", "Remove", key)
                    end
                    C.owned[key] = nil
                    return
                end
            end
            local count = 0
            for _ in pairs(active) do
                count += 1
            end
            for key, d in pairs(desired) do
                if not active[key] and os.clock() >= (C.retry[key] or 0) and count < MS.SimulSpin(player) then
                    local allowed = not d.info.Map or L.PlayerData.UnlockedMap[d.info.Map]
                    local target = selectedTarget(d.config)
                    if
                        allowed
                        and (not d.config.SelectGacha or target)
                        and (L.PlayerData.Items[d.info.Currency] or 0) > 0
                    then
                        C.retry[key] = os.clock() + 10
                        C.owned[key] = true
                        L.Remote:Fire(
                            "SpinManagerSystem",
                            "Add",
                            d.id,
                            d.kind,
                            GS:GetSpinTargets(d.id, d.kind),
                            target
                        )
                        return
                    end
                end
            end
        end
        local function upgradeStep()
            if
                not C.upgradeOn
                or not C.system
                or #C.priorities == 0
                or not AS.CanUseUpgrade(L.PlayerData, C.system)
            then
                return
            end
            local data = L.PlayerData
            if C.pending then
                local p = C.pending
                if
                    (data.Upgrades[p.key] or 0) > p.level
                    or (
                        p.progression
                        and os.clock() >= p.confirmAfter
                        and (data.Items[p.currency] or 0) < p.balance
                    )
                then
                    C.cursor = C.cursor % #C.priorities + 1
                    C.pending = nil
                elseif os.clock() < p.untilTime then
                    return
                else
                    C.pending = nil
                end
            end
            for _ = 1, #C.priorities do
                C.cursor = (C.cursor - 1) % #C.priorities + 1
                local target = C.priorities[C.cursor]
                local d = upgrades[C.system].Targets[target]
                local key = C.system .. "_" .. target
                local level = data.Upgrades[key] or 0
                if d and level < d.MaxLevel then
                    local price = US.CalculatePrice(C.system, target, level)
                    if price and (data.Items[d.Currency or upgrades[C.system].Currency] or 0) >= price then
                        local currency = d.Currency or upgrades[C.system].Currency
                        C.pending = {
                            key = key,
                            level = level,
                            untilTime = os.clock() + 5,
                            confirmAfter = os.clock() + 0.5,
                            progression = AS.IsProgression(C.system),
                            currency = currency,
                            balance = data.Items[currency] or 0,
                        }
                        L.Remote:Fire("UpgradeSystem", "Buy", C.system, target)
                    end
                    return
                end
                C.cursor = C.cursor % #C.priorities + 1
            end
        end
        task.spawn(function()
            identity(2)
            while S.running and S.scrollControl == C do
                local ok, err = pcall(function()
                    spinStep()
                    upgradeStep()
                    craftStep()
                end)
                C.error = not ok and tostring(err) or nil
                C.lastTick = os.clock()
                task.wait(ok and 0.5 or 5)
            end
            for key in pairs(C.owned) do
                pcall(function()
                    L.Remote:Fire("SpinManagerSystem", "Remove", key)
                end)
            end
        end)
    end
end

function Runtime:hideRewards()
    local Library = self.Library
    local GuiService = self.GuiService
    local window = self.window
    local state = self.state
    do
        local s = self.state
        if s.controls.hideGamemodeRewards then
            return
        end
        local identity = setthreadidentity or setidentity
        identity(2)
        local L = self.Library
        local screen = L:GetScreen("Results")
        local GS = L:GetService("GuiService")
        identity(8)
        local utilities = self.tabs.automation
        local enabled = false
        local function hide()
            if not enabled or not s.running or not screen.Parent or not screen.Enabled then
                return
            end
            screen.Enabled = false
            task.defer(function()
                if not s.running then
                    return
                end
                identity(2)
                GS.SetScreens(not L.LocalPlayer:GetAttribute("GuiOpened"), { "SideGUI", "Utils" }, true)
            end)
        end
        s.controls.hideGamemodeRewards = utilities:AddToggle({
            Title = "Hide Gamemode Rewards",
            Description = "Hide the Raid and Trial results screen. Rewards are still received.",
            Default = false,
            Callback = function(value)
                enabled = value
                s.hideGamemodeRewards = value
                hide()
            end,
        })
        local connection = screen:GetPropertyChangedSignal("Enabled"):Connect(hide)
        s.window.Gui.Destroying:Connect(function()
            enabled = false
            connection:Disconnect()
        end)
    end
end

function Runtime:hideTeleport()
    local Players = self.Players
    local window = self.window
    local state = self.state
    do
        local s = self.state
        if s.controls.hideTeleportScreen then
            return
        end
        local identity = setthreadidentity or setidentity
        if identity then
            identity(8)
        end
        local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
        local utilities = self.tabs.automation
        local enabled = false
        local screen, connection, restoreEnabled
        local function hide()
            if enabled and s.running and screen and screen.Parent and screen.Enabled then
                screen.Enabled = false
            end
        end
        local function bind(candidate)
            if candidate.Name ~= "Transition" or not candidate:IsA("ScreenGui") then
                return
            end
            if connection then
                connection:Disconnect()
            end
            screen = candidate
            restoreEnabled = screen.Enabled
            connection = screen:GetPropertyChangedSignal("Enabled"):Connect(hide)
            hide()
        end
        local existing = playerGui:FindFirstChild("Transition")
        if existing then
            bind(existing)
        end
        local added = playerGui.ChildAdded:Connect(bind)
        s.controls.hideTeleportScreen = utilities:AddToggle({
            Title = "Hide Teleport Screen",
            Description = "Hide Raid, Trial and world teleport overlays. Teleport timing is unchanged.",
            Default = false,
            Callback = function(value)
                if value and not enabled and screen then
                    restoreEnabled = screen.Enabled
                end
                enabled = value
                s.hideTeleportScreen = value
                if value then
                    hide()
                elseif screen and screen.Parent then
                    screen.Enabled = restoreEnabled
                end
            end,
        })
        s.window.Gui.Destroying:Connect(function()
            enabled = false
            if connection then
                connection:Disconnect()
            end
            added:Disconnect()
            if screen and screen.Parent then
                screen.Enabled = restoreEnabled
            end
        end)
    end
end

function Runtime:repairInput()
    if self.window.IsWindUI or self.window.IsZeen then
        return
    end
    local window = self.window
    local state = self.state
    do
        local s = self.state
        local gui = assert(s.window and s.window.Gui, "Foccus window is missing")
        local identity = assert(setthreadidentity or setidentity, "Thread identity unavailable")
        local touchEnabled = game:GetService("UserInputService").TouchEnabled
        if s.uiInputRepair and s.uiInputRepair.gui == gui then
            s.uiInputRepair.scan()
        else
            local repair =
                { gui = gui, connections = {}, seen = setmetatable({}, { __mode = "k" }), count = 0 }
            s.uiInputRepair = repair
            local function fixSignal(signal)
                local ok, connections = pcall(getconnections, signal)
                if not ok then
                    return
                end
                for _, old in ipairs(connections) do
                    local fn = old.Function
                    if
                        old.Enabled
                        and type(fn) == "function"
                        and not old.ForeignState
                        and not repair.seen[fn]
                    then
                        repair.seen[fn] = true
                        local wrapped = function(...)
                            identity(8)
                            return fn(...)
                        end
                        repair.seen[wrapped] = true
                        local replacement = signal:Connect(wrapped)
                        old:Disable()
                        table.insert(repair.connections, replacement)
                        repair.count += 1
                    end
                end
            end
            local function fixObject(obj)
                if obj:IsA("GuiObject") and not touchEnabled then
                    for _, name in ipairs({
                        "InputBegan",
                        "InputChanged",
                        "InputEnded",
                        "MouseEnter",
                        "MouseLeave",
                    }) do
                        fixSignal(obj[name])
                    end
                end
                if obj:IsA("GuiButton") then
                    if touchEnabled then
                        fixSignal(obj.Activated)
                    else
                        for _, name in ipairs({
                            "Activated",
                            "MouseButton1Click",
                            "MouseButton1Down",
                            "MouseButton1Up",
                            "MouseButton2Click",
                        }) do
                            fixSignal(obj[name])
                        end
                    end
                end
                if obj:IsA("TextBox") then
                    fixSignal(obj.Focused)
                    fixSignal(obj.FocusLost)
                    fixSignal(obj:GetPropertyChangedSignal("Text"))
                end
            end
            function repair.scan()
                identity(8)
                for _, obj in ipairs(gui:QueryDescendants("GuiObject")) do
                    fixObject(obj)
                end
            end
            repair.scan()
            repair.added = gui.DescendantAdded:Connect(function(obj)
                task.defer(function()
                    identity(8)
                    if obj.Parent then
                        fixObject(obj)
                    end
                end)
            end)
            gui.Destroying:Connect(function()
                repair.added:Disconnect()
                for _, c in ipairs(repair.connections) do
                    c:Disconnect()
                end
            end)
        end
    end
end

function Runtime:buildMobileButton()
    if self.state.mobileButton and self.state.mobileButton.gui.Parent then
        return
    end
    local gui = self.window.Gui
    local UIS = game:GetService("UserInputService")
    local overlay = Instance.new("ScreenGui")
    overlay.Name = "ZeenFloating"
    overlay.ResetOnSpawn = false
    overlay.DisplayOrder = 2147483647
    overlay.IgnoreGuiInset = true
    gui.DisplayOrder = 2147483645
    for _, extra in ipairs(self.window.extraRoots or {}) do
        extra.DisplayOrder = 2147483646
    end
    overlay.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    overlay.Parent = gui.Parent
    local area = Instance.new("Frame")
    area.Size = UDim2.fromScale(1, 1)
    area.BackgroundTransparency = 1
    area.Parent = overlay
    local button = Instance.new("ImageButton")
    button.Name = "ToggleWindow"
    button.Size = UDim2.fromOffset(56, 56)
    button.Position = UDim2.new(0, 22, 0.5, -28)
    button.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
    button.BackgroundTransparency = 0
    button.AutoButtonColor = false
    button.Image = "rbxassetid://92270900275589"
    button.ScaleType = Enum.ScaleType.Fit
    button.ClipsDescendants = true
    button.BorderSizePixel = 0
    button.Active = true
    button.Parent = area
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = button
    local border = Instance.new("UIStroke")
    border.Color = Color3.fromRGB(175, 175, 175)
    border.Transparency = 0
    border.Thickness = 2
    border.Parent = button
    local connections = {}
    local drag, startPoint, startPosition, moved
    local function position(point)
        local bounds = area.AbsoluteSize
        button.Position = UDim2.fromOffset(
            math.clamp(point.X, 0, math.max(0, bounds.X - 56)),
            math.clamp(point.Y, 0, math.max(0, bounds.Y - 56))
        )
    end
    local function toggle()
        self.setIdentity(8)
        if not gui.Parent then
            return
        end
        self.window:Toggle()
    end
    connections[#connections + 1] = button.InputBegan:Connect(function(input)
        self.setIdentity(8)
        if drag then
            return
        end
        if
            input.UserInputType == Enum.UserInputType.Touch
            or input.UserInputType == Enum.UserInputType.MouseButton1
        then
            drag = input
            startPoint = Vector2.new(input.Position.X, input.Position.Y)
            startPosition = button.AbsolutePosition - area.AbsolutePosition
            moved = false
        end
    end)
    connections[#connections + 1] = UIS.InputChanged:Connect(function(input)
        if not drag then
            return
        end
        if
            input ~= drag
            and not (
                drag.UserInputType == Enum.UserInputType.MouseButton1
                and input.UserInputType == Enum.UserInputType.MouseMovement
            )
        then
            return
        end
        self.setIdentity(8)
        local delta = Vector2.new(input.Position.X, input.Position.Y) - startPoint
        if delta.Magnitude > 7 then
            moved = true
        end
        if moved then
            position(startPosition + delta)
        end
    end)
    connections[#connections + 1] = UIS.InputEnded:Connect(function(input)
        self.setIdentity(8)
        if input ~= drag then
            return
        end
        drag = nil
        local point = Vector2.new(input.Position.X, input.Position.Y)
        local p, size = button.AbsolutePosition, button.AbsoluteSize
        if
            not moved
            and (point - startPoint).Magnitude <= 7
            and point.X >= p.X
            and point.Y >= p.Y
            and point.X <= p.X + size.X
            and point.Y <= p.Y + size.Y
        then
            toggle()
        end
    end)
    connections[#connections + 1] = UIS.WindowFocusReleased:Connect(function()
        drag = nil
        moved = true
    end)
    connections[#connections + 1] = area:GetPropertyChangedSignal("AbsoluteSize"):Connect(function()
        self.setIdentity(8)
        position(button.AbsolutePosition - area.AbsolutePosition)
    end)
    gui.Destroying:Connect(function()
        self.setIdentity(8)
        for _, connection in ipairs(connections) do
            connection:Disconnect()
        end
        overlay:Destroy()
    end)
    self.state.mobileButton = { gui = overlay, button = button, toggle = toggle }
end

function Runtime:bindShortcut()
    if self.window.IsRayfield or self.window.IsWindUI or self.window.IsZeen then
        local UIS = game:GetService("UserInputService")
        local gui, window = self.window.Gui, self.window
        local shortcut = { connections = {} }
        self.state.ctrlShortcut = shortcut
        shortcut.handler = function(input, processed)
            self.setIdentity(8)
            if not gui.Parent or processed or UIS:GetFocusedTextBox() then
                return
            end
            if input.UserInputType ~= Enum.UserInputType.Keyboard then
                return
            end
            if input.KeyCode == Enum.KeyCode.RightControl and self.window.IsWindUI then
                window:Toggle()
            elseif input.KeyCode == Enum.KeyCode.LeftControl and not self.window.IsWindUI then
                window:Toggle()
            end
        end
        shortcut.connections[1] = UIS.InputBegan:Connect(shortcut.handler)
        gui.Destroying:Connect(function()
            for _, connection in ipairs(shortcut.connections) do
                connection:Disconnect()
            end
        end)
        return
    end
    local window = self.window
    local state = self.state
    do
        local s = self.state
        local w = s.window
        local gui = w.Gui
        local identity = setthreadidentity or setidentity
        identity(8)
        if not s.ctrlShortcut then
            local UIS = game:GetService("UserInputService")
            local shortcut = { connections = {} }
            s.ctrlShortcut = shortcut
            local source = debug.info(w.SelectTab, "s")
            if type(getconnections) == "function" and type(debug.getconstants) == "function" then
                for _, connection in ipairs(getconnections(UIS.InputBegan)) do
                    local fn = connection.Function
                    if
                        connection.Enabled
                        and type(fn) == "function"
                        and not connection.ForeignState
                        and debug.info(fn, "s") == source
                    then
                        local constants = debug.getconstants(fn)
                        if
                            table.find(constants, "LeftControl")
                            and table.find(constants, "RightControl")
                            and table.find(constants, "GetFocusedTextBox")
                        then
                            local handler = function(input, processed)
                                identity(8)
                                if not gui.Parent then
                                    return
                                end
                                return fn(input, processed)
                            end
                            table.insert(shortcut.connections, UIS.InputBegan:Connect(handler))
                            connection:Disable()
                            shortcut.handler = handler
                        end
                    end
                end
            end
            if not shortcut.handler then
                shortcut.handler = function(input, processed)
                    identity(8)
                    if not gui.Parent or processed or UIS:GetFocusedTextBox() then
                        return
                    end
                    if
                        input.KeyCode == Enum.KeyCode.LeftControl
                        or input.KeyCode == Enum.KeyCode.RightControl
                    then
                        gui.Enabled = not gui.Enabled
                    end
                end
                table.insert(shortcut.connections, UIS.InputBegan:Connect(shortcut.handler))
            end
            gui.Destroying:Connect(function()
                for _, connection in ipairs(shortcut.connections) do
                    connection:Disconnect()
                end
            end)
        end
    end
end

function Runtime:buildModeBoosts(tab)
    local state, L, player = self.state, self.Library, self.player
    local old = state.modeBoost
    local enabled = old and old.enabled or false
    local raid = old and table.clone(old.raid) or {}
    local trial = old and table.clone(old.trial) or {}
    local portal = old and old.portal and table.clone(old.portal) or {}
    if old then
        old.enabled = false
        old.pending = nil
    end
    for _, key in ipairs({ "modeBoost", "raidBoost", "trialBoost", "portalBoost" }) do
        local control = state.controls[key]
        if control and control.Instance then
            control.Instance:Destroy()
        end
    end
    local catalog = self:getBoostCatalog()
    local options = {}
    for id, info in pairs(catalog) do
        local count = tonumber((L.PlayerData.Items or {})[id]) or 0
        table.insert(options, {
            Title = info.Name or id,
            Value = id,
            Description = id .. " | Owned: " .. tostring(count),
            Order = tonumber(info.Order) or 999,
            SubOrder = tonumber(info.SubOrder) or 999,
        })
    end
    table.sort(options, function(a, b)
        if a.Order ~= b.Order then
            return a.Order < b.Order
        end
        if a.SubOrder ~= b.SubOrder then
            return a.SubOrder < b.SubOrder
        end
        return a.Title < b.Title
    end)
    local m = {
        enabled = enabled,
        raid = raid,
        trial = trial,
        portal = portal,
        invasion = {},
        managed = {},
        retry = {},
        previous = "__boot",
        version = 2,
        optionCount = #options,
        nextAction = 0,
    }
    state.modeBoost = m
    local function selectItems(values)
        local result = {}
        for _, id in ipairs(values) do
            if catalog[id] then
                result[#result + 1] = id
            end
        end
        return result
    end
    m.raid, m.trial = selectItems(raid), selectItems(trial)
    m.portal = selectItems(portal)
    state.controls.modeBoost = tab:AddToggle({
        Title = "Auto Use Boost",
        Default = m.enabled,
        Description = "Uses selected boosts in Raid, Trial and Portal. Pauses outside and resumes on return.",
        Callback = function(value)
            m.enabled = value
            m.previous = "__boot"
            m.nextAction = 0
        end,
    })
    state.controls.raidBoost = tab:AddDropdown({
        Title = "Raid Boosts",
        Description = "All boost items, including those not owned.",
        Placeholder = "Select boosts",
        Multi = true,
        Default = m.raid,
        Options = options,
        Callback = function(values)
            m.raid = selectItems(values)
        end,
    })
    state.controls.trialBoost = tab:AddDropdown({
        Title = "Trial Boosts",
        Description = "Pause after the Trial; resume when entering the next Trial.",
        Placeholder = "Select boosts",
        Multi = true,
        Default = m.trial,
        Options = options,
        Callback = function(values)
            m.trial = selectItems(values)
        end,
    })
    state.controls.portalBoost = tab:AddDropdown({
        Title = "Portal Boosts",
        Description = "Use or resume these boosts in Portal; pause outside.",
        Placeholder = "Select boosts",
        Multi = true,
        Default = m.portal,
        Options = options,
        Callback = function(values)
            m.portal = selectItems(values)
        end,
    })
    function m:step(mode, data, now, fire)
        if not self.enabled then
            return
        end
        if mode ~= self.previous then
            self.previous = mode
            self.readyAt = now + 1
        end
        local active = {}
        for _, id in ipairs(self.raid) do
            self.managed[id] = true
            if mode == "Raid" then
                active[id] = true
            end
        end
        for _, id in ipairs(self.trial) do
            self.managed[id] = true
            if mode == "Time Trial" then
                active[id] = true
            end
        end
        for _, id in ipairs(self.portal) do
            self.managed[id] = true
            if mode == "Portal" then
                active[id] = true
            end
        end
        for _, id in ipairs(self.invasion or {}) do
            self.managed[id] = true
            if mode == "Invasion" then
                active[id] = true
            end
        end
        for _, id in ipairs(self.tower or {}) do
            self.managed[id] = true
            if mode == "Tower" then
                active[id] = true
            end
        end
        for _, id in ipairs(self.defense or {}) do
            self.managed[id] = true
            if mode == "Defense" then active[id] = true end
        end
        if now < self.nextAction then
            return
        end
        local durations, paused = data.Consumables or {}, data.ConsumablePaused or {}
        local ids = {}
        for id in pairs(self.managed) do
            ids[#ids + 1] = id
        end
        table.sort(ids)
        -- Pause outgoing items before starting the incoming mode's boosts.
        for _, wantActive in ipairs({ false, true }) do
            for _, id in ipairs(ids) do
                local wanted = active[id] == true
                local remaining = tonumber(durations[id]) or 0
                local isPaused = paused[id] == true
                local weatherOwner = state.weatherBoost and state.weatherBoost:owns(id)
                if not weatherOwner and wanted == wantActive and now >= (self.retry[id] or 0) then
                    if remaining > 0 and isPaused == wanted then
                        fire("ConsumableSystem", "Pause", id)
                        self.retry[id] = now + 3
                        self.nextAction = now + 0.4
                        self.lastAction = { item = id, action = wanted and "resume" or "pause" }
                        return
                    elseif
                        wanted
                        and remaining <= 0
                        and now >= (self.readyAt or 0)
                        and (tonumber((data.Items or {})[id]) or 0) > 0
                    then
                        fire("ItemSystem", "Use", id, nil, nil)
                        self.retry[id] = now + 3
                        self.nextAction = now + 0.4
                        self.lastAction = { item = id, action = "use" }
                        return
                    end
                end
            end
        end
    end
    task.spawn(function()
        self.setIdentity(2)
        while state.running and state.modeBoost == m do
            local ok, err = pcall(function()
                m:step(player:GetAttribute("Mode"), L.PlayerData, os.clock(), function(...)
                    L.Remote:Fire(...)
                end)
            end)
            m.error = not ok and tostring(err) or nil
            task.wait(ok and 0.2 or 2)
        end
    end)
end

function Runtime:buildFarmModeUI()
    local s = self.state
    s.farmMode = s.farmMode or "Traditional"
    if s.controls.farmMode then
        return
    end
    self.tabs.farming:RouteSection("World Farm")
    s.controls.farmMode = self.tabs.farming:AddDropdown({
        Title = "Select Farm Mode",
        Multi = false,
        Default = s.farmMode,
        Options = {
            { Title = "Tradicional", Value = "Traditional" },
            { Title = "End Game", Value = "EndGame" },
        },
        Callback = function(value)
            s.farmMode = value
            s.target = nil
            s.rangeSpot = nil
            s.raidEndGameSpot = nil
            s.rangePosition = nil
        end,
    })
    local npcFrame = s.controls.npcs and s.controls.npcs.Instance
    local modeFrame = s.controls.farmMode.Instance
    if npcFrame and modeFrame and npcFrame.Parent == modeFrame.Parent then
        local order = npcFrame.LayoutOrder
        for _, sibling in ipairs(npcFrame.Parent:GetChildren()) do
            if sibling:IsA("GuiObject") and sibling ~= modeFrame and sibling.LayoutOrder > order then
                sibling.LayoutOrder += 1
            end
        end
        modeFrame.LayoutOrder = order + 1
    end
    self.tabs.farming:RouteSection("Secret Bosses")
end

function Runtime:raidEndGamePosition(context, cache)
    local s = self.state
    local radius = 8 * (tonumber(self.player:GetAttribute("AttackRange")) or 1)
    local sessionId = self.player:GetAttribute("InMode")
    local maps = workspace:FindFirstChild("_MAP")
    local modes = maps and maps:FindFirstChild("Gamemode")
    local map = modes and sessionId and modes:FindFirstChild(tostring(sessionId))
    local spots = map and map:FindFirstChild("Spots")
    local fixed = s.raidEndGameSpot
    if fixed and fixed.key == context.key and fixed.map == map and fixed.spots == spots then
        return fixed.position, radius
    end
    local points = {}
    if spots then
        for _, spot in ipairs(spots:GetChildren()) do
            if spot:IsA("BasePart") then
                points[#points + 1] = spot.Position
            end
        end
    end
    if #points == 0 then
        -- Do not chase the current target while the raid map is loading.
        local character = self.player.Character
        local root = character and character:FindFirstChild("HumanoidRootPart")
        return root and root.Position or nil, radius
    end
    local minX, maxX, minZ, maxZ = math.huge, -math.huge, math.huge, -math.huge
    local heights = {}
    for _, p in ipairs(points) do
        minX = math.min(minX, p.X)
        maxX = math.max(maxX, p.X)
        minZ = math.min(minZ, p.Z)
        maxZ = math.max(maxZ, p.Z)
        heights[#heights + 1] = p.Y
    end
    table.sort(heights)
    local y = heights[math.ceil(#heights / 2)]
    local center = Vector3.new((minX + maxX) / 2, y, (minZ + maxZ) / 2)
    local function reach(p)
        local farthest = 0
        for _, v in ipairs(points) do
            farthest = math.max(farthest, (p.X - v.X) ^ 2 + (p.Z - v.Z) ^ 2)
        end
        return farthest
    end
    local best = reach(center)
    local function candidate(x, z)
        local p = Vector3.new(x, y, z)
        local required = reach(p)
        if required < best then
            center = p
            best = required
        end
    end
    -- A minimum enclosing circle is determined by two or three spawn points.
    -- Bound the exhaustive pass for maps with unusually many markers.
    if #points <= 24 then
        for i = 1, #points do
            for j = i + 1, #points do
                local a, b = points[i], points[j]
                candidate((a.X + b.X) / 2, (a.Z + b.Z) / 2)
                for k = j + 1, #points do
                    local c = points[k]
                    local d = 2 * (a.X * (b.Z - c.Z) + b.X * (c.Z - a.Z) + c.X * (a.Z - b.Z))
                    if math.abs(d) > 0.0001 then
                        local aa, bb, cc = a.X * a.X + a.Z * a.Z, b.X * b.X + b.Z * b.Z, c.X * c.X + c.Z * c.Z
                        candidate(
                            (aa * (b.Z - c.Z) + bb * (c.Z - a.Z) + cc * (a.Z - b.Z)) / d,
                            (aa * (c.X - b.X) + bb * (a.X - c.X) + cc * (b.X - a.X)) / d
                        )
                    end
                end
            end
        end
    end
    s.raidEndGameSpot = {
        key = context.key,
        map = map,
        spots = spots,
        position = center + Vector3.new(0, 2, 0),
        requiredRange = math.sqrt(best),
    }
    return s.raidEndGameSpot.position, radius
end

function Runtime:rangeFarmPosition(context, target, cache)
    local s = self.state
    if context.ghoul or s.farmMode ~= "EndGame" then
        s.raidEndGameSpot = nil
        s.rangeSpot = nil
        return nil
    end
    if context.key:sub(1, 5) == "raid:" then
        return self:raidEndGamePosition(context, cache)
    end
    s.raidEndGameSpot = nil
    local radius = 8 * (tonumber(self.player:GetAttribute("AttackRange")) or 1)
    local remembered = s.rangeSpot
    if not target then
        if remembered and remembered.key == context.key and remembered.radius == radius then
            return remembered.center + Vector3.new(0, 2, 0), radius
        end
        return nil
    end
    local function dist2(a, b)
        local x, z = a.X - b.X, a.Z - b.Z
        return x * x + z * z
    end
    local function eligible(enemy)
        if not enemy.Parent or not enemy:IsA("BasePart") then
            return false
        end
        if
            enemy:GetAttribute("Dead")
            or enemy:GetAttribute("Shield")
            or (tonumber(enemy:GetAttribute("HP")) or 0) <= 0
        then
            return false
        end
        if context.scope then
            return enemy:IsDescendantOf(context.scope)
        end
        if context.secretTarget then
            return enemy == context.secretTarget
        end
        return enemy:GetAttribute("Type") == "Normal"
            and enemy:GetAttribute("Map") == context.world
            and context.selected
            and context.selected[enemy:GetAttribute("Id")] == true
    end
    if not eligible(target) then
        return nil
    end
    local origin = target.Position
    local reach = math.max(0, radius - 0.5)
    local reach2 = reach * reach
    local function covers(center, p)
        return dist2(center, p) <= reach2 and math.abs(p.Y - (center.Y + 2)) <= radius
    end
    local same = remembered and remembered.key == context.key and remembered.radius == radius
    if same and os.clock() < remembered.untilTime and covers(remembered.center, origin) then
        return remembered.center + Vector3.new(0, 2, 0), radius
    end
    local nearby = {}
    for enemy in pairs(cache) do
        if enemy ~= target and eligible(enemy) then
            local p = enemy.Position
            local d = dist2(origin, p)
            if d <= 4 * reach2 and math.abs(p.Y - origin.Y) <= radius / 2 then
                nearby[#nearby + 1] = { point = p, distance = d, name = enemy.Name }
            end
        end
    end
    table.sort(nearby, function(a, b)
        if a.distance == b.distance then
            return a.name < b.name
        end
        return a.distance < b.distance
    end)
    local points = { origin }
    for i = 1, math.min(#nearby, 31) do
        points[#points + 1] = nearby[i].point
    end
    local anchor = same and remembered.center or origin
    local best, bestCount, bestTravel = origin, -1, math.huge
    local evaluations = 0
    local function consider(x, z)
        local p = Vector3.new(x, origin.Y, z)
        if not covers(p, origin) then
            return
        end
        local count = 0
        for _, v in ipairs(points) do
            evaluations += 1
            if covers(p, v) then
                count += 1
            end
        end
        local travel = dist2(p, anchor)
        if count > bestCount or (count == bestCount and travel < bestTravel) then
            best, bestCount, bestTravel = p, count, travel
        end
    end
    if same and covers(remembered.center, origin) and math.abs(remembered.center.Y - origin.Y) < 0.5 then
        consider(remembered.center.X, remembered.center.Z)
    end
    consider(origin.X, origin.Z)
    local mean = Vector3.zero
    for _, p in ipairs(points) do
        mean += p
    end
    mean /= #points
    consider(mean.X, mean.Z)
    -- Target-anchored candidates keep priority targets in range with bounded work.
    for i = 2, #points do
        local p = points[i]
        consider(p.X, p.Z)
        local mx, mz = (origin.X + p.X) / 2, (origin.Z + p.Z) / 2
        consider(mx, mz)
        local d2 = dist2(origin, p)
        if d2 > 0.000001 and d2 <= 4 * reach2 then
            local scale = math.sqrt(math.max(0, reach2 - d2 / 4) / d2)
            local dx, dz = -(p.Z - origin.Z) * scale, (p.X - origin.X) * scale
            -- A tiny inward offset avoids losing boundary points to rounding.
            consider(mx + dx * 0.999999, mz + dz * 0.999999)
            consider(mx - dx * 0.999999, mz - dz * 0.999999)
        end
    end
    s.rangeSpot = {
        key = context.key,
        center = best,
        radius = radius,
        count = bestCount,
        untilTime = os.clock() + 0.2,
        evaluations = evaluations,
    }
    return best + Vector3.new(0, 2, 0), radius
end

function Runtime:getTeleportQueue()
    return queue_on_teleport
        or queueonteleport
        or (syn and syn.queue_on_teleport)
        or (fluxus and fluxus.queue_on_teleport)
end

function Runtime:makeTeleportPayload()
    local m = self.state.autoExecute
    local source = getgenv().ZeenSource or getgenv().TBLSource
    assert(
        m.url ~= "" or (type(source) == "string" and #source > 0),
        "Run the complete Zeen release or enter a Loader URL before enabling Auto Execute."
    )
    local values = {}
    for _, control in ipairs(self.window.controls) do
        if control.flag and (not control.Instance or control.Instance.Parent) then
            values[control.flag] = control:Get()
        end
    end
    local json = game:GetService("HttpService"):JSONEncode(values)
    local payload = [=[
repeat task.wait() until game:IsLoaded()
local G=getgenv()
if G.ZeenTeleportBooting or G.ZeenTeleportBootJob==game.JobId then return end
G.ZeenTeleportBooting=true
local ok,err=pcall(function()
    local source=__ZEEN_SOURCE__
    local url=__ZEEN_URL__
    if url~="" then
        local lastError
        for attempt=1,3 do
            local fetched,value=pcall(function() return game:HttpGet(url) end)
            if fetched and type(value)=="string" and #value>0 then source=value; break end
            lastError=tostring(value)
            if attempt<3 then task.wait(2) end
        end
        assert(type(source)=="string" and #source>0,lastError or "Empty Zeen download")
    end
    local framework=assert(game:GetService("ReplicatedStorage"):WaitForChild("Framework",60),"Framework not ready")
    local module=assert(framework:WaitForChild("Library",60),"Library not ready")
    local identity=setthreadidentity or setidentity
    if identity then identity(2) end
    local L=require(module)
    local deadline=os.clock()+90
    repeat task.wait(0.2) until (game.Players.LocalPlayer and type(L.PlayerData)=="table" and L.PlayerData.Items and L.PlayerData.UnlockedMap) or os.clock()>deadline
    assert(game.Players.LocalPlayer and type(L.PlayerData)=="table" and L.PlayerData.Items and L.PlayerData.UnlockedMap,"Player data not ready")
    if identity then identity(8) end
    G.ZeenSource=source
    G.TBLSource=source
    G.ZeenTeleportSettings=game:GetService("HttpService"):JSONDecode(__ZEEN_SETTINGS__)
    assert(loadstring(source,"@R1mHub"))()
    G.ZeenTeleportBootJob=game.JobId
end)
G.ZeenTeleportBooting=nil
if not ok then warn("Zeen Auto Execute: "..tostring(err)) end
]=]
    local replacements = { SOURCE = m.url == "" and source or "", URL = m.url, SETTINGS = json }
    payload = payload:gsub("__ZEEN_(%u+)__", function(key)
        return string.format("%q", replacements[key])
    end)
    return payload, json
end

function Runtime:bindAutoExecute()
    local m = self.state.autoExecute
    for _, connection in ipairs(m.connections or {}) do
        connection:Disconnect()
    end
    m.connections = {}
    m.queued = false
    m.version = 2
    m.connections[1] = self.player.OnTeleport:Connect(function(status)
        if
            (status ~= Enum.TeleportState.Started and status ~= Enum.TeleportState.InProgress)
            or not m.enabled
            or m.queued
            or m.preparing
        then
            return
        end
        m.preparing = true
        local ok, err = pcall(function()
            self.setIdentity(8)
            local queue = assert(self:getTeleportQueue(), "Executor has no queue_on_teleport support.")
            local payload, json = self:makeTeleportPayload()
            -- Queue before optional disk I/O; the payload also carries settings for fileless executors.
            queue(payload)
            m.queued = true
            m.error = nil
            if type(writefile) == "function" then
                pcall(function()
                    if isfolder and makefolder and not isfolder("Foccus") then
                        makefolder("Foccus")
                    end
                    writefile("Foccus/anime-breaker-rayfield.json", json)
                end)
            end
        end)
        m.preparing = false
        if not ok then
            m.error = tostring(err)
            self.window:Notify({ Title = "Auto Execute failed", Description = m.error, Duration = 6 })
        end
    end)
    m.connections[2] = game:GetService("TeleportService").TeleportInitFailed:Connect(function(p)
        if p == self.player then
            m.queued = false
            m.preparing = false
        end
    end)
    m.connections[3] = self.window.Gui.Destroying:Connect(function()
        for _, connection in ipairs(m.connections) do
            connection:Disconnect()
        end
    end)
end

function Runtime:setAutoExecuteEnabled(value)
    local m = self.state.autoExecute
    m.enabled = false
    if value then
        local ok, err = pcall(function()
            assert(
                type(self:getTeleportQueue()) == "function",
                "Your executor has no queue_on_teleport support."
            )
            self:makeTeleportPayload()
        end)
        if not ok then
            m.error = tostring(err)
            local control = self.state.controls.autoExecute
            if control then
                control:Set(false, true)
            end
            self.window:Notify({ Title = "Auto Execute", Description = m.error, Duration = 6 })
            return
        end
    end
    m.enabled = value
    m.error = nil
end

function Runtime:buildAutoExecute()
    local s, tab = self.state, self.tabs.config
    local m = { enabled = false, url = "", queued = false }
    s.autoExecute = m
    tab:AddSection("Auto Execute")
    tab:AddParagraph({
        Title = "Execute after teleport",
        Description = "The complete Zeen release carries its source. A Loader URL can override it. Requires executor queue_on_teleport support.",
    })
    s.controls.autoExecuteUrl = tab:AddInput({
        Title = "Loader URL (optional)",
        Default = "",
        Placeholder = "https://raw.githubusercontent.com/...",
        Callback = function(v)
            v = tostring(v or ""):match("^%s*(.-)%s*$")
            if v == "" or v:match("^https://") then
                m.url = v
                if m.enabled then
                    self:setAutoExecuteEnabled(true)
                end
            end
        end,
    })
    s.controls.autoExecute = tab:AddToggle({
        Title = "Auto Execute on Server Change",
        Default = false,
        Callback = function(v)
            self:setAutoExecuteEnabled(v)
        end,
    })
    self:bindAutoExecute()
end

function Runtime:buildMagicTower()
    self.setIdentity(2)
    self.towers = self.Library:GetData("GamemodeData").Tower or {}
    self.setIdentity(8)
    local s, tab = self.state, self.tabs.modes
    local m = {
        modes = {},
        cursor = 1,
        enter = false,
        farm = false,
        leave = false,
        wave = 100,
        priority = false,
        wait = false,
        min = 2,
        join = false,
        private = false,
        equip = "Damage",
        nextAction = 0,
    }
    s.tower = m
    local options = {}
    for id, info in pairs(self.towers) do
        options[#options + 1] = { Title = info.Name or id, Value = id, Order = info.Order or 999 }
    end
    table.sort(options, function(a, b)
        return a.Order < b.Order
    end)
    local function register(key, control)
        s.controls[key] = control
        table.insert(s.extraConfigKeys, key)
        return control
    end
    local function toggle(key, title, field, description)
        register(
            key,
            tab:AddToggle({
                Title = title,
                Default = m[field],
                Description = description,
                Callback = function(value)
                    m[field] = value
                    m.nextAction = 0
                    s.target = nil
                end,
            })
        )
    end
    local function numberInput(key, title, field, limit)
        local control
        control = tab:AddInput({
            Title = title,
            Default = tostring(m[field]),
            Finished = true,
            Callback = function(text)
                local n = tonumber(text)
                if n and n == n and n % 1 == 0 and n >= 1 and n <= limit then
                    m[field] = n
                elseif control then
                    control:Set(tostring(m[field]), true)
                end
            end,
        })
        register(key, control)
    end
    tab:AddSection("Magic Tower")
    tab:AddParagraph({
        Title = "Fire / Water / Wind",
        Description = "Select one or more towers. Runs alternate after leaving a tower. Creating a room requires a Magic Tower Key and the Black Clover world. Towers have no separate difficulty.",
    })
    register(
        "towerModes",
        tab:AddDropdown({
            Title = "Select Tower Modes",
            Multi = true,
            Default = {},
            Options = options,
            Callback = function(values)
                m.modes = {}
                for _, option in ipairs(options) do
                    if table.find(values or {}, option.Value) then
                        m.modes[#m.modes + 1] = option.Value
                    end
                end
                m.cursor = 1
                m.nextAction = 0
                s.target = nil
            end,
        })
    )
    toggle(
        "towerEnter",
        "Auto Join Magic Tower",
        "enter",
        "Create and start the next selected tower when a key is available."
    )
    toggle(
        "towerFarm",
        "Auto Farm Magic Tower",
        "farm",
        "Attack NPCs in your current selected tower. Supports the shared End Game farm setting."
    )
    numberInput("towerWave", "Tower Leave at Wave", "wave", 10000)
    toggle(
        "towerLeave",
        "Auto Leave Tower at Wave",
        "leave",
        "Leave at the configured floor and rotate to the next selected tower."
    )
    toggle(
        "towerPriority",
        "Prioritize Magic Tower",
        "priority",
        "May leave a Raid or Portal to enter a tower. Trial and Marine Invasion keep priority."
    )
    tab:AddSection("Tower Players")
    toggle(
        "towerJoinPublic",
        "Join Public Towers First",
        "join",
        "Auto Join checks selected public rooms before creating your own room."
    )
    toggle("towerPrivate", "Private Tower Room", "private", "Create a private room instead of a public room.")
    toggle(
        "towerWait",
        "Wait for Tower Players",
        "wait",
        "Wait before starting your own room. Other hosts and the game's Auto setting control their own starts."
    )
    numberInput("towerPlayers", "Tower Minimum Players", "min", self.Players.MaxPlayers)
    tab:AddSection("Tower Automation")
    local equip = { { Title = "Do Nothing", Value = "__none" } }
    for id, info in pairs(self.boostData) do
        if info.EquipBest then
            equip[#equip + 1] = { Title = info.Name or id, Value = id }
        end
    end
    register(
        "towerEquip",
        tab:AddDropdown({
            Title = "Tower Equip Best",
            Default = "Damage",
            Options = equip,
            Callback = function(value)
                m.equip = value
                s.modeEquip.previous = "__boot"
            end,
        })
    )
    local boosts = {}
    for id, info in pairs(self:getBoostCatalog()) do
        if type(info.Boost) == "table" and next(info.Boost) then
            boosts[#boosts + 1] = { Title = info.Name or id, Value = id }
        end
    end
    table.sort(boosts, function(a, b)
        return a.Title < b.Title
    end)
    s.modeBoost.tower = {}
    register(
        "towerBoost",
        tab:AddDropdown({
            Title = "Tower Boosts",
            Multi = true,
            Default = {},
            Options = boosts,
            Description = "Use or resume in the tower; pause outside. Weather rules retain priority.",
            Callback = function(values)
                s.modeBoost.tower = values
            end,
        })
    )
end

function Runtime:resolveMagicTower(mode, session, sessionId, now)
    local s, L, G = self.state, self.Library, self.GamemodeService
    local m = s.tower
    if not m then
        return false
    end
    local function clearTarget()
        s.target = nil
        s.rangeSpot = nil
        s.raidEndGameSpot = nil
        s.nextAttackAt = 0
    end
    if mode ~= "Tower" and m.activeSession then
        local index = table.find(m.modes, m.activeMap)
        if #m.modes > 0 then
            m.cursor = index and index % #m.modes + 1 or 1
        end
        m.activeSession = nil
        m.activeMap = nil
        m.finished = false
        m.nextAction = now + 3
        s.resumeFarmJump = true
        s.resumeFarmAt = now + 0.25
        clearTarget()
    end
    if mode == "Tower" then
        if not session then
            return true
        end
        local map = session:GetAttribute("MapId")
        if not table.find(m.modes, map) then
            return true
        end
        if m.activeSession ~= sessionId then
            m.activeSession = sessionId
            m.activeMap = map
            m.finished = false
            m.nextAction = 0
            clearTarget()
        end
        local status = tostring(session:GetAttribute("Status") or "")
        local ended = status == "Completed"
            or status == "Complete"
            or status == "Finished"
            or status == "Ended"
            or status == "Closed"
        local stage = tonumber(session:GetAttribute("Stage")) or 0
        if m.finished or (ended and (m.enter or m.farm or m.leave)) or (m.leave and stage >= m.wave) then
            m.finished = true
            clearTarget()
            s.status = "Leaving Magic Tower: " .. tostring(map)
            if now >= m.nextAction then
                m.nextAction = now + 3
                L.Remote:Fire("GamemodeSystem", "Quit")
            end
            return true
        end
        if status == "Opened" then
            if m.enter and session:GetAttribute("HostId") == self.player.UserId then
                local members = session:FindFirstChild("Players")
                local count = 0
                if members then
                    for _ in pairs(members:GetAttributes()) do
                        count += 1
                    end
                end
                if m.wait and count < m.min then
                    s.status = "Tower waiting for players: " .. count .. "/" .. m.min
                elseif now >= m.nextAction then
                    m.nextAction = now + 3
                    L.Remote:Fire("GamemodeSystem", "Start", "Tower")
                end
            end
            return true
        end
        if not m.farm then
            return true
        end
        local enemies = workspace:FindFirstChild("_ENEMIES")
        local server = enemies and enemies:FindFirstChild("Server")
        local folder = server and server:FindFirstChild("Gamemode")
        local scope = folder and folder:FindFirstChild(tostring(sessionId))
        return true, scope and { key = "tower:" .. tostring(sessionId), scope = scope } or nil
    end
    if not m.enter or #m.modes == 0 then
        return false
    end
    if now < m.nextAction then
        return mode == nil or mode == ""
    end
    if mode and mode ~= "" and (not m.priority or (mode ~= "Raid" and mode ~= "Portal")) then
        return false
    end
    if self.player:GetAttribute("Teleporting") then
        return false
    end
    local id = m.modes[m.cursor] or m.modes[1]
    local info = self.towers[id]
    if not info or not (L.PlayerData.UnlockedMap or {})[info.RequiredMap] then
        return false
    end
    local room
    if m.join then
        for _, candidate in ipairs(G.GetRooms("Tower", id)) do
            local status = candidate:GetAttribute("Status")
            if
                candidate:GetAttribute("HostId") ~= self.player.UserId
                and candidate:GetAttribute("Private") == false
                and status == "Opened"
            then
                room = candidate
                break
            end
        end
    end
    local hasKey = (tonumber((L.PlayerData.Items or {})[info.RequiredItem]) or 0) > 0
    if not room and (not hasKey or not G.CanOpenRoom("Tower", id, self.player.UserId)) then
        return false
    end
    m.nextAction = now + 3
    clearTarget()
    if mode and mode ~= "" then
        s.status = "Leaving " .. tostring(mode) .. " for Magic Tower"
        L.Remote:Fire("GamemodeSystem", "Quit")
    elseif room then
        s.status = "Joining public " .. id
        L.Remote:Fire("GamemodeSystem", "Join", "Tower", room:GetAttribute("HostId"))
    else
        s.status = "Creating " .. id
        L.Remote:Fire("GamemodeSystem", "Create", "Tower", id, G.GetFirstDiff("Tower", id), m.private)
    end
    return true
end

function Runtime:buildDefense()
    self.setIdentity(2)
    self.defenses = self.Library:GetData("GamemodeData").Defense or {}
    self.setIdentity(8)
    local s, tab = self.state, self.tabs.modes
    local m = {
        modes = { "Cursed Defense" },
        cursor = 1,
        enter = false,
        farm = false,
        leave = false,
        wave = 100,
        priority = false,
        wait = false,
        min = 2,
        join = false,
        private = false,
        equip = "Damage",
        nextAction = 0,
    }
    s.defense = m
    local options = {}
    for id, info in pairs(self.defenses) do
        options[#options + 1] = { Title = info.Name or id, Value = id, Order = info.Order or 999 }
    end
    table.sort(options, function(a, b)
        return a.Order < b.Order
    end)
    local function register(key, control)
        s.controls[key] = control
        table.insert(s.extraConfigKeys, key)
        return control
    end
    local function toggle(key, title, field, description)
        register(
            key,
            tab:AddToggle({
                Title = title,
                Default = m[field],
                Description = description,
                Callback = function(value)
                    m[field] = value
                    m.nextAction = 0
                    s.target = nil
                end,
            })
        )
    end
    local function numberInput(key, title, field, limit)
        local control
        control = tab:AddInput({
            Title = title,
            Default = tostring(m[field]),
            Finished = true,
            Callback = function(text)
                local n = tonumber(text)
                if n and n == n and n % 1 == 0 and n >= 1 and n <= limit then
                    m[field] = n
                elseif control then
                    control:Set(tostring(m[field]), true)
                end
            end,
        })
        register(key, control)
    end
    tab:AddSection("Defense")
    register("autoDefense", tab:AddToggle({
        Title="Auto Defense", Default=false,
        Description="Automatically enter, start and farm the selected Defense. Repeat after completion.",
        Callback=function(value)
            for _, entry in ipairs({ {"defenseEnter", "enter"}, {"defenseFarm", "farm"} }) do
                local control=s.controls[entry[1]]
                if control then control:Set(value, true) end
                m[entry[2]]=value
            end
            m.nextAction=0
            s.target=nil
        end,
    }))
    tab:AddParagraph({
        Title = "Cursed Defense",
        Description = "Requires a Cursed Defense Key and the JJK world. Auto Defense creates or joins a room, starts it, farms enemies and repeats after completion. Keys drop in the JJK Raid.",
    })
    register(
        "defenseModes",
        tab:AddDropdown({
            Title = "Select Defense",
            Multi = true,
            Default = { "Cursed Defense" },
            Options = options,
            Callback = function(values)
                m.modes = {}
                for _, option in ipairs(options) do
                    if table.find(values or {}, option.Value) then
                        m.modes[#m.modes + 1] = option.Value
                    end
                end
                m.cursor = 1
                m.nextAction = 0
                s.target = nil
            end,
        })
    )
    toggle(
        "defenseEnter",
        "Auto Join Defense",
        "enter",
        "Create and start the next selected defense when a key is available."
    )
    toggle(
        "defenseFarm",
        "Auto Farm Defense",
        "farm",
        "Attack NPCs in your current selected defense. Supports the shared End Game farm setting."
    )
    numberInput("defenseWave", "Defense Leave at Wave", "wave", 10000)
    toggle(
        "defenseLeave",
        "Auto Leave Defense at Wave",
        "leave",
        "Leave at the configured floor and rotate to the next selected defense."
    )
    toggle(
        "defensePriority",
        "Prioritize Defense",
        "priority",
        "May leave a Raid or Portal to enter a defense. Trial and Marine Invasion keep priority."
    )
    tab:AddSection("Defense Players")
    toggle(
        "defenseJoinPublic",
        "Join Public Defenses First",
        "join",
        "Auto Join checks selected public rooms before creating your own room."
    )
    toggle("defensePrivate", "Private Defense Room", "private", "Create a private room instead of a public room.")
    toggle(
        "defenseWait",
        "Wait for Defense Players",
        "wait",
        "Wait before starting your own room. Other hosts and the game's Auto setting control their own starts."
    )
    numberInput("defensePlayers", "Defense Minimum Players", "min", self.Players.MaxPlayers)
    tab:AddSection("Defense Automation")
    local equip = { { Title = "Do Nothing", Value = "__none" } }
    for id, info in pairs(self.boostData) do
        if info.EquipBest then
            equip[#equip + 1] = { Title = info.Name or id, Value = id }
        end
    end
    register(
        "defenseEquip",
        tab:AddDropdown({
            Title = "Defense Equip Best",
            Default = "Damage",
            Options = equip,
            Callback = function(value)
                m.equip = value
                s.modeEquip.previous = "__boot"
            end,
        })
    )
    local boosts = {}
    for id, info in pairs(self:getBoostCatalog()) do
        if type(info.Boost) == "table" and next(info.Boost) then
            boosts[#boosts + 1] = { Title = info.Name or id, Value = id }
        end
    end
    table.sort(boosts, function(a, b)
        return a.Title < b.Title
    end)
    s.modeBoost.defense = {}
    register(
        "defenseBoost",
        tab:AddDropdown({
            Title = "Defense Boosts",
            Multi = true,
            Default = {},
            Options = boosts,
            Description = "Use or resume in the defense; pause outside. Weather rules retain priority.",
            Callback = function(values)
                s.modeBoost.defense = values
            end,
        })
    )
end

function Runtime:resolveDefense(mode, session, sessionId, now)
    local s, L, G = self.state, self.Library, self.GamemodeService
    local m = s.defense
    if not m then
        return false
    end
    local function clearTarget()
        s.target = nil
        s.rangeSpot = nil
        s.raidEndGameSpot = nil
        s.nextAttackAt = 0
    end
    if mode ~= "Defense" and m.activeSession then
        local index = table.find(m.modes, m.activeMap)
        if #m.modes > 0 then
            m.cursor = index and index % #m.modes + 1 or 1
        end
        m.activeSession = nil
        m.activeMap = nil
        m.finished = false
        m.nextAction = now + 3
        s.resumeFarmJump = true
        s.resumeFarmAt = now + 0.25
        clearTarget()
    end
    if mode == "Defense" then
        if not session then
            return true
        end
        local map = session:GetAttribute("MapId")
        if not table.find(m.modes, map) then
            return true
        end
        if m.activeSession ~= sessionId then
            m.activeSession = sessionId
            m.activeMap = map
            m.finished = false
            m.nextAction = 0
            clearTarget()
        end
        local status = tostring(session:GetAttribute("Status") or "")
        local ended = status == "Completed"
            or status == "Complete"
            or status == "Finished"
            or status == "Ended"
            or status == "Closed"
        local stage = tonumber(session:GetAttribute("Stage")) or 0
        if m.finished or (ended and (m.enter or m.farm or m.leave)) or (m.leave and stage >= m.wave) then
            m.finished = true
            clearTarget()
            s.status = "Leaving Defense: " .. tostring(map)
            if now >= m.nextAction then
                m.nextAction = now + 3
                L.Remote:Fire("GamemodeSystem", "Quit")
            end
            return true
        end
        if status == "Opened" then
            if m.enter and session:GetAttribute("HostId") == self.player.UserId then
                local members = session:FindFirstChild("Players")
                local count = 0
                if members then
                    for _ in pairs(members:GetAttributes()) do
                        count += 1
                    end
                end
                if m.wait and count < m.min then
                    s.status = "Defense waiting for players: " .. count .. "/" .. m.min
                elseif now >= m.nextAction then
                    m.nextAction = now + 3
                    L.Remote:Fire("GamemodeSystem", "Start", "Defense")
                end
            end
            return true
        end
        if not m.farm then
            return true
        end
        local enemies = workspace:FindFirstChild("_ENEMIES")
        local server = enemies and enemies:FindFirstChild("Server")
        local folder = server and server:FindFirstChild("Gamemode")
        local scope = folder and folder:FindFirstChild(tostring(sessionId))
        return true, scope and { key = "defense:" .. tostring(sessionId), scope = scope } or nil
    end
    if not m.enter or #m.modes == 0 then
        return false
    end
    if now < m.nextAction then
        return mode == nil or mode == ""
    end
    if mode and mode ~= "" and (not m.priority or (mode ~= "Raid" and mode ~= "Portal")) then
        return false
    end
    if self.player:GetAttribute("Teleporting") then
        return false
    end
    local id = m.modes[m.cursor] or m.modes[1]
    local info = self.defenses[id]
    if not info or not (L.PlayerData.UnlockedMap or {})[info.RequiredMap] then
        return false
    end
    local room
    if m.join then
        for _, candidate in ipairs(G.GetRooms("Defense", id)) do
            local status = candidate:GetAttribute("Status")
            if
                candidate:GetAttribute("HostId") ~= self.player.UserId
                and candidate:GetAttribute("Private") == false
                and (status == "Opened" or (info.JoinRunning and status == "Running"))
            then
                room = candidate
                break
            end
        end
    end
    local hasKey = (tonumber((L.PlayerData.Items or {})[info.RequiredItem]) or 0) > 0
    if not room and not hasKey then
        s.status="Defense: Cursed Defense Key required (JJK Raid)"
        return false
    end
    if not room and not G.CanOpenRoom("Defense", id, self.player.UserId) then
        return false
    end
    m.nextAction = now + 3
    clearTarget()
    if mode and mode ~= "" then
        s.status = "Leaving " .. tostring(mode) .. " for Defense"
        L.Remote:Fire("GamemodeSystem", "Quit")
    elseif room then
        s.status = "Joining public " .. id
        L.Remote:Fire("GamemodeSystem", "Join", "Defense", room:GetAttribute("HostId"))
    else
        s.status = "Creating " .. id
        L.Remote:Fire("GamemodeSystem", "Create", "Defense", id, G.GetFirstDiff("Defense", id), m.private)
    end
    return true
end

function Runtime:buildMarineInvasion()
    local s, tab = self.state, self.tabs.invasion
    local m = {
        priority = true,
        enter = false,
        farm = false,
        leave = false,
        wave = 100,
        wait = false,
        min = 2,
        nextAction = 0,
        skipUntil = 0,
        equip = "Damage",
    }
    s.invasion = m
    tab:AddSection("Marine Invasion")
    tab:AddParagraph({
        Title = "Scheduled event",
        Description = "Trial keeps priority. Entry follows the game's schedule. Wait for Players pauses Zeen farming only; the server controls the event start.",
    })
    for _, v in ipairs({
        { "invasionEnter", "Auto Enter Invasion", "enter" },
        { "invasionFarm", "Auto Farm Invasion", "farm" },
        { "invasionLeave", "Auto Leave Invasion", "leave" },
        { "invasionWait", "Wait for Players", "wait" },
    }) do
        local key, title, field = v[1], v[2], v[3]
        s.controls[key] = tab:AddToggle({
            Title = title,
            Default = false,
            Callback = function(value)
                m[field] = value
            end,
        })
    end
    for _, v in ipairs({
        { "invasionWave", "Leave at Wave", "wave", 100, 10000 },
        { "invasionPlayers", "Minimum Players", "min", 2, self.Players.MaxPlayers },
    }) do
        local key, title, field, default, limit = unpack(v)
        local control
        control = tab:AddInput({
            Title = title,
            Default = tostring(default),
            Callback = function(value)
                local n = tonumber(value)
                if n and n % 1 == 0 and n >= 1 and n <= limit then
                    m[field] = n
                elseif control then
                    control:Set(tostring(m[field]), true)
                end
            end,
        })
        s.controls[key] = control
    end
    s.controls.invasionPriority = tab:AddToggle({
        Title = "Prioritize Marine Invasion",
        Default = true,
        Description = "When Auto Enter is enabled, leave Raid or Portal for an open Invasion. Trial retains highest priority.",
        Callback = function(v)
            m.priority = v
        end,
    })
    tab:AddSection("Invasion Automation")
    local options = { { Title = "Do Nothing", Value = "__none" } }
    for id, v in pairs(self.boostData) do
        if v.EquipBest then
            options[#options + 1] = { Title = v.Name or id, Value = id }
        end
    end
    s.controls.invasionEquip = tab:AddDropdown({
        Title = "Invasion Equip Best",
        Options = options,
        Default = "Damage",
        Callback = function(v)
            m.equip = v
        end,
    })
    tab:AddParagraph({
        Title = "Mode automation",
        Description = "Use the shared Auto Equip Best and Auto Use Boosts switches on this page. Weather boost rules retain priority.",
    })
    local boosts = {}
    for id, v in pairs(self:getBoostCatalog()) do
        if type(v.Boost) == "table" and next(v.Boost) then
            boosts[#boosts + 1] = { Title = v.Name or id, Value = id }
        end
    end
    s.controls.invasionBoost = tab:AddDropdown({
        Title = "Invasion Boosts",
        Multi = true,
        Default = {},
        Options = boosts,
        Callback = function(v)
            s.modeBoost.invasion = v
        end,
    })
end

function Runtime:resolveInvasion(mode, session, sessionId, now)
    local m, s, L = self.state.invasion, self.state, self.Library
    if not m then
        return false
    end
    local G = self.GamemodeService
    local diff = G.GetFirstDiff("Invasion", "Marine Invasion")
    if mode == "Invasion" then
        if not session then
            return true
        end
        local stage = tonumber(session:GetAttribute("Stage")) or 0
        if m.leave and stage >= m.wave then
            if now >= m.nextAction then
                m.nextAction = now + 3
                local window = G.GetWindow("Invasion", "Marine Invasion", diff)
                m.skipUntil = window and window.ClosesAt or G.GetTime() + 60
                L.Remote:Fire("GamemodeSystem", "Quit")
            end
            return true
        end
        if not m.farm then
            return true
        end
        if m.wait then
            local members = session:FindFirstChild("Players")
            local count = 0
            if members then
                for _ in pairs(members:GetAttributes()) do
                    count += 1
                end
            end
            if count < m.min then
                s.status = "Invasion waiting for players: " .. count .. "/" .. m.min
                return true
            end
        end
        local folder = workspace._ENEMIES.Server:FindFirstChild("Gamemode")
        local scope = folder and folder:FindFirstChild(tostring(sessionId))
        return true, scope and { key = "invasion:" .. tostring(sessionId), scope = scope } or nil
    end
    if mode == "Time Trial" or not m.enter or G.GetTime() < m.skipUntil then
        return false
    end
    if mode and not m.priority then
        return false
    end
    local trial = s.trial
    if
        trial
        and trial.enter
        and G.GetTime() >= trial.skipUntil
        and G.IsOpen("Time Trial", "The Hallway", G.GetFirstDiff("Time Trial", "The Hallway"))
    then
        return false
    end
    if not (L.PlayerData.UnlockedMap or {}).OnePiece then
        return false
    end
    if not G.IsOpen("Invasion", "Marine Invasion", diff) then
        return false
    end
    s.target = nil
    if now >= m.nextAction then
        m.nextAction = now + 1.5
        if mode then
            s.status = "Leaving " .. tostring(mode) .. " for Marine Invasion"
            L.Remote:Fire("GamemodeSystem", "Quit")
        else
            s.status = "Entering Marine Invasion"
            L.Remote:Fire("GamemodeSystem", "Enter", "Invasion", "Marine Invasion", diff)
        end
    end
    return true
end

function Runtime:buildExpedition()
    local s, L, tab = self.state, self.Library, self.tabs.expedition
    self.setIdentity(2)
    local A = L:GetService("AutoService")
    local catalog = L:GetData("AutoData")
    local items = L:GetData("ItemData")
    self.setIdentity(8)
    local native = {}
    local entries = {}
    for id, v in pairs(catalog) do
        if v.Expedition == "Harbor" and v.Kind then
            entries[#entries + 1] = { id = id, info = v }
        end
    end
    table.sort(entries, function(a, b)
        return (a.info.Order or 0) < (b.info.Order or 0)
    end)
    tab:AddSection("Harbor Auto")
    tab:AddParagraph({
        Title = "Native Harbor automation",
        Description = "These controls update the game's own Auto settings. They are saved by the game and respect unlock requirements. Configure each dock's ship and route in Harbor first. Auto Upgrade spends Berries.",
    })
    for _, entry in ipairs(entries) do
        local id, info = entry.id, entry.info
        if info.Kind == "Toggle" then
            local control
            control = tab:AddToggle({
                Title = (
                    info.Group == "AutoHarborSendGroup" and "Auto Send - "
                    or info.Group == "AutoHarborCollectGroup" and "Auto Collect - "
                    or ""
                ) .. info.Name,
                Default = (L.PlayerData.AutoSettings or {})[id] == true,
                Callback = function(v)
                    if not self.window.ready or self.window.restoring then
                        return
                    end
                    self.setIdentity(2)
                    if ((L.PlayerData.AutoSettings or {})[id] == true) ~= v then
                        L.Remote:Fire("AutoSystem", "Toggle", id)
                    end
                end,
            })
            native[#native + 1] = { id = id, info = info, control = control }
        elseif info.Kind == "Select" then
            local opts = {}
            self.setIdentity(2)
            for _, v in ipairs(A.GetOptions(info, L.PlayerData.AutoSettings, L.PlayerData)) do
                opts[#opts + 1] = { Title = A.GetLabel(info, v), Value = v }
            end
            local value = A.GetValue(info, L.PlayerData.AutoSettings, L.PlayerData)
            self.setIdentity(8)
            local control = tab:AddDropdown({
                Title = info.Name,
                Options = opts,
                Default = value,
                Callback = function(v)
                    if self.window.ready and not self.window.restoring then
                        L.Remote:Fire("AutoSystem", "Set", id, v)
                    end
                end,
            })
            native[#native + 1] = { id = id, info = info, control = control }
        end
    end
    tab:AddSection("Harbor Priorities")
    for _, id in ipairs({ "AutoHarborUnitPriority", "AutoHarborUpgradePriority", "AutoHarborVehiclePriority" }) do
        local info = catalog[id]
        if info then
            local chosen = nil
            local function options()
                self.setIdentity(2)
                local result = {}
                for i, v in ipairs(A.GetPriorityList(info, L.PlayerData.AutoSettings, L.PlayerData)) do
                    result[#result + 1] = {
                        Title = tostring(i)
                            .. ". "
                            .. A.GetPriorityLabel(info, v, L.PlayerData.AutoSettings, L.PlayerData),
                        Value = v,
                    }
                end
                self.setIdentity(8)
                return result
            end
            local dropdown = tab:AddDropdown({
                Title = info.Name,
                Options = options(),
                Callback = function(v)
                    chosen = v
                end,
            })
            tab:AddButton({
                Title = "Move Up - " .. info.Name,
                Callback = function()
                    if chosen then
                        L.Remote:Fire("AutoSystem", "Move", id, chosen, -1)
                    end
                end,
            })
            tab:AddButton({
                Title = "Move Down - " .. info.Name,
                Callback = function()
                    if chosen then
                        L.Remote:Fire("AutoSystem", "Move", id, chosen, 1)
                    end
                end,
            })
            if info.Disable then
                tab:AddButton({
                    Title = "Enable / Disable - " .. info.Name,
                    Callback = function()
                        if chosen then
                            L.Remote:Fire("AutoSystem", "TogglePriority", id, chosen)
                        end
                    end,
                })
            end
            tab:AddButton({
                Title = "Refresh - " .. info.Name,
                Callback = function()
                    dropdown:Reload(options())
                    local off = A.GetPriorityOff(info, L.PlayerData.AutoSettings, L.PlayerData)
                    local disabled = {}
                    for key, value in pairs(off or {}) do
                        if value then
                            disabled[#disabled + 1] = tostring(key)
                        end
                    end
                    self.window:Notify({
                        Title = info.Name,
                        Description = "Disabled: "
                            .. (#disabled > 0 and table.concat(disabled, ", ") or "none"),
                        Duration = 4,
                    })
                end,
            })
        end
    end
    task.spawn(function()
        self.setIdentity(2)
        while s.running do
            if self.window.ready then
                local ok, err = pcall(function()
                    for _, entry in ipairs(native) do
                        local value = entry.info.Kind == "Toggle"
                            and ((L.PlayerData.AutoSettings or {})[entry.id] == true)
                        if entry.info.Kind ~= "Toggle" then
                            value = A.GetValue(entry.info, L.PlayerData.AutoSettings, L.PlayerData)
                        end
                        if entry.control:Get() ~= value then
                            entry.control:Set(value, true)
                        end
                    end
                end)
                s.expeditionError = not ok and tostring(err) or nil
            end
            task.wait(2)
        end
    end)
    local boxes = { currency = false, fruit = false, selected = {}, rewards = {}, cursor = 0, pending = nil }
    s.autoBoxes = boxes
    tab:AddSection("Auto Open Boxes")
    tab:AddParagraph({
        Title = "Currency rewards",
        Description = "Select box → reward combinations in one dropdown. Multiple rewards rotate fairly. Only selected combinations are opened, one box at a time with inventory confirmation.",
    })
    local opts, selectionLookup = {}, {}
    for id, item in pairs(items) do
        if id:match("^MapBoxCurrency") and not item.Unobtainable then
            for index, drop in ipairs(item.Drops or {}) do
                if drop.Id then
                    local key = id .. "|" .. drop.Id
                    selectionLookup[key] = { id = id, reward = drop.Id }
                    opts[#opts + 1] = {
                        Title = (item.Name or id)
                            .. " → "
                            .. (items[drop.Id] and items[drop.Id].Name or drop.Id),
                        Value = key,
                    }
                end
            end
        end
    end
    table.sort(opts, function(a, b)
        return a.Title < b.Title
    end)
    s.controls.currencyBoxes = tab:AddDropdown({
        Title = "Currency Box Rewards",
        Flag = "expedition.Boxes.Auto Open Boxes.Currency Box Rewards v2",
        Multi = true,
        Default = {},
        Options = opts,
        Callback = function(values)
            boxes.selected = {}
            for _, key in ipairs(values) do
                if selectionLookup[key] then
                    boxes.selected[#boxes.selected + 1] = key
                end
            end
        end,
    })
    -- Convert the old per-box selectors without choosing any new reward.
    s.currencyMigration = function(data)
        if data["expedition.Boxes.Auto Open Boxes.Currency Box Rewards v2"] ~= nil then
            return
        end
        local selected = data["expedition.Boxes.Auto Open Boxes.Currency Boxes"]
        if type(selected) ~= "table" then
            return
        end
        local converted = {}
        for _, id in ipairs(selected) do
            local item = items[id]
            local reward = item and data["expedition.Boxes.Auto Open Boxes." .. item.Name .. " Reward"]
            local key = reward and (id .. "|" .. tostring(reward))
            if key and selectionLookup[key] then
                converted[#converted + 1] = key
            end
        end
        data["expedition.Boxes.Auto Open Boxes.Currency Box Rewards v2"] = converted
    end
    self.window.migrateConfig = s.currencyMigration
    s.controls.currencyBoxAuto = tab:AddToggle({
        Title = "Auto Open Currency Boxes",
        Default = false,
        Callback = function(v)
            boxes.currency = v
        end,
    })
    s.controls.fruitBoxAuto = tab:AddToggle({
        Title = "Auto Open Fruit Boxes",
        Default = false,
        Callback = function(v)
            boxes.fruit = v
        end,
    })
    task.spawn(function()
        self.setIdentity(2)
        while s.running do
            if self.window.ready then
                local ok, err = pcall(function()
                    local inventory = L.PlayerData.Items or {}
                    local pending = boxes.pending
                    if pending then
                        if (tonumber(inventory[pending.id]) or 0) < pending.before then
                            boxes.pending = nil
                            boxes.error = nil
                        elseif os.clock() < pending.untilTime then
                            return
                        else
                            boxes.pending = nil
                            boxes.currency = false
                            boxes.fruit = false
                            s.controls.currencyBoxAuto:Set(false, true)
                            s.controls.fruitBoxAuto:Set(false, true)
                            self.window:Notify({
                                Title = "Auto Open stopped",
                                Description = "Inventory did not confirm the last box. Re-enable to retry.",
                                Duration = 6,
                            })
                            return
                        end
                    end
                    local candidates = {}
                    if boxes.currency then
                        for _, key in ipairs(boxes.selected) do
                            local selection = selectionLookup[key]
                            local id = selection and selection.id
                            local item = id and items[id]
                            if item and id:match("^MapBoxCurrency") then
                                for index, drop in ipairs(item.Drops or {}) do
                                    if drop.Id == selection.reward then
                                        candidates[#candidates + 1] = { id = id, choice = index }
                                        break
                                    end
                                end
                            end
                        end
                    end
                    if boxes.fruit then
                        candidates[#candidates + 1] = { id = "DevilFruitBox" }
                    end
                    for i = 1, #candidates do
                        local index = ((boxes.cursor + i - 1) % #candidates) + 1
                        local entry = candidates[index]
                        local count = tonumber(inventory[entry.id]) or 0
                        if count > 0 then
                            boxes.cursor = index
                            boxes.pending = { id = entry.id, before = count, untilTime = os.clock() + 10 }
                            L.Remote:Fire("ItemSystem", "Use", entry.id, 1, entry.choice)
                            return
                        end
                    end
                end)
                if not ok then
                    boxes.error = tostring(err)
                end
            end
            task.wait(1)
        end
    end)
end

function Runtime:snapshotExtra()
    local result = {}
    for _, key in ipairs(self.state.extraConfigKeys or {}) do
        local control = self.state.controls[key]
        if control then
            result[key] = control:Get()
        end
    end
    return result
end

function Runtime:restoreExtra(values)
    if type(values) ~= "table" then
        return
    end
    values = table.clone(values)
    if type(values.currencyBoxes) == "table" then
        local converted = {}
        for _, key in ipairs(values.currencyBoxes) do
            if key:find("|", 1, true) then
                converted[#converted + 1] = key
            else
                local reward = values["boxReward_" .. key]
                if reward and reward ~= "__none" then
                    converted[#converted + 1] = key .. "|" .. reward
                end
            end
        end
        values.currencyBoxes = converted
    end
    for _, booleanPass in ipairs({ false, true }) do
        for _, key in ipairs(self.state.extraConfigKeys or {}) do
            local value = values[key]
            local control = self.state.controls[key]
            if value ~= nil and control and (type(value) == "boolean") == booleanPass then
                control:Set(value)
            end
        end
    end
end

function Runtime:getBoostCatalog()
    self.setIdentity(2)
    local catalog = {}
    for id, info in pairs(self.Library:GetData("ItemData")) do
        if
            type(info) == "table"
            and info.Type == "Consumable"
            and type(info.Boost) == "table"
            and next(info.Boost)
            and not info.Unobtainable
        then
            catalog[id] = info
        end
    end
    for id, info in pairs(self.consumableData) do
        if type(info.Boost) == "table" and next(info.Boost) and not info.Unobtainable then
            catalog[id] = info
        end
    end
    self.setIdentity(8)
    return catalog
end

function Runtime:stepInvasionShop(now)
    local shop, L = self.state.invasionShop, self.Library
    if not shop.enabled or #shop.items == 0 or now < shop.nextBuy then
        return
    end
    local data = L.PlayerData
    local config = shop.config
    local version = shop.service.GetVersion(config)
    local saved = data.StockShops and data.StockShops.Pirate
    if shop.pending then
        local p = shop.pending
        local current = saved and saved.Version == version and saved.Items and saved.Items[p.key]
        if
            version ~= p.version
            or (current ~= nil and current < p.stock)
            or (tonumber(data.Items[p.id]) or 0) > p.before
        then
            shop.pending = nil
        elseif now < p.deadline then
            return
        else
            shop.enabled = false
            shop.pending = nil
            self.state.controls.invasionShopBuy:Set(false, true)
            self.window:Notify({
                Title = "Auto Buy Juices stopped",
                Description = "The last purchase was not confirmed. Check your balance and shop access before retrying.",
                Duration = 6,
            })
            return
        end
    end
    for _ = 1, #shop.items do
        local key = shop.items[shop.cursor]
        shop.cursor = shop.cursor % #shop.items + 1
        local entry = config.Items[key]
        if entry then
            local stock = entry.Stock or 0
            if saved and saved.Version == version and saved.Items and saved.Items[key] ~= nil then
                stock = saved.Items[key]
            end
            if stock > 0 and (tonumber(data.Items[config.Currency]) or 0) >= entry.Price then
                shop.pending = {
                    key = key,
                    id = entry.Id,
                    version = version,
                    stock = stock,
                    before = tonumber(data.Items[entry.Id]) or 0,
                    deadline = now + 10,
                }
                shop.nextBuy = now + 1
                L.Remote:Fire("StockShopSystem", "Buy", "Pirate", key, 1)
                return
            end
        end
    end
    shop.nextBuy = now + 2
end

function Runtime:buildInvasionShop()
    local s, L, tab = self.state, self.Library, self.tabs.invasion
    self.setIdentity(2)
    local config = L:GetData("StockShopData").Pirate
    local items = L:GetData("ItemData")
    local service = L:GetService("StockShopService")
    self.setIdentity(8)
    local shop = { enabled = false, items = {}, cursor = 1, nextBuy = 0, config = config, service = service }
    s.invasionShop = shop
    tab:AddSection("Invasion Shop")
    local options = {}
    for key, entry in pairs(config.Items) do
        local info = items[entry.Id]
        if info and (info.Category == "Juice" or entry.Id:find("Juice", 1, true)) then
            options[#options + 1] =
                { Title = info.Name, Value = key, Description = tostring(entry.Price) .. " Pirate Shards" }
        end
    end
    table.sort(options, function(a, b)
        return a.Title < b.Title
    end)
    s.controls.invasionShopItems = tab:AddDropdown({
        Title = "Juices to Buy",
        Multi = true,
        Default = {},
        Options = options,
        Callback = function(values)
            shop.items = {}
            for _, id in ipairs(values) do
                if config.Items[id] then
                    shop.items[#shop.items + 1] = id
                end
            end
            shop.cursor = 1
        end,
    })
    s.controls.invasionShopBuy = tab:AddToggle({
        Title = "Auto Buy Juices",
        Default = false,
        Description = "Uses Pirate Shards, one purchase at a time. Respects stock and balance; no paid restocks.",
        Callback = function(v)
            shop.enabled = v
        end,
    })
    task.spawn(function()
        self.setIdentity(2)
        while s.running do
            if self.window.ready then
                local ok, err = pcall(self.stepInvasionShop, self, os.clock())
                shop.error = not ok and tostring(err) or nil
                if not ok then
                    shop.nextBuy = os.clock() + 5
                end
            end
            task.wait(0.5)
        end
    end)
end

function Runtime:buildHalloween()
    self.setIdentity(2)
    local L, state, tab = self.Library, self.state, self.tabs.halloween
    local itemData, upgrades = L:GetData("ItemData"), L:GetData("UpgradeData")
    local shops, shopOptions, itemOptions = L:GetData("StockShopData"), {}, {}
    self.setIdentity(8)
    local byId = {}
    for id, config in pairs(shops or {}) do
        if type(config)=="table" and type(config.Items)=="table" then
            local name=tostring(config.Name or id)
            if name:lower():find("halloween",1,true) or tostring(id):lower():find("halloween",1,true) then
                byId[id]=config; shopOptions[#shopOptions+1]={Title=name,Value=id}
                for key,entry in pairs(config.Items) do
                    local item=itemData[entry.Id]
                    itemOptions[#itemOptions+1]={Title=(item and item.Name or tostring(entry.Id or key)).." - "..name,Value=tostring(id).."|"..tostring(key),Description=tostring(entry.Price or "?").." "..tostring(config.Currency or "")}
                end
            end
        end
    end
    local function sort(t) table.sort(t,function(a,b)return a.Title<b.Title end) end
    sort(shopOptions);sort(itemOptions)
    local shop={enabled=false,items={},cursor=1,nextBuy=0,pending=nil}
    tab:AddSection("Halloween Shop")
    state.controls.halloweenShop=tab:AddDropdown({Title="Halloween Shop",Multi=false,Options=shopOptions,Callback=function(id)shop.id=id;shop.items={};shop.pending=nil end})
    tab:AddDropdown({Title="Select Items",Multi=true,Default={},Options=itemOptions,Callback=function(values)
        shop.items={};for _,value in ipairs(values or {}) do local id,key=tostring(value):match("^(.-)|(.+)$");if id==shop.id and byId[id] and byId[id].Items[key] then shop.items[#shop.items+1]=key end end;table.sort(shop.items);shop.cursor=1
    end})
    state.controls.halloweenShopBuy=tab:AddToggle({Title="Auto Buy Halloween Items",Default=false,Description="Buys selected items using the event currency and available stock.",Callback=function(v)shop.enabled=v end})
    local function stepShop(now)
        if not shop.enabled or not shop.id or #shop.items==0 or now<shop.nextBuy then return end
        local config,data=byId[shop.id],L.PlayerData;if not config or not data then return end
        local version=L:GetService("StockShopService").GetVersion(config);local saved=data.StockShops and data.StockShops[shop.id]
        if shop.pending then local p=shop.pending;local stock=saved and saved.Version==version and saved.Items and saved.Items[p.key]
            if version~=p.version or (stock and stock<p.stock) or (tonumber(data.Items[p.item]) or 0)>p.before then shop.pending=nil
            elseif now<p.deadline then return
            else shop.enabled=false;state.controls.halloweenShopBuy:Set(false,true);return end
        end
        for _=1,#shop.items do local key=shop.items[shop.cursor];shop.cursor=shop.cursor%#shop.items+1;local entry=config.Items[key];local stock=entry and (entry.Stock or 0)
            if saved and saved.Version==version and saved.Items and saved.Items[key]~=nil then stock=saved.Items[key] end
            if entry and stock>0 and (tonumber(data.Items[config.Currency]) or 0)>=(entry.Price or math.huge) then
                shop.pending={key=key,item=entry.Id,version=version,stock=stock,before=tonumber(data.Items[entry.Id]) or 0,deadline=now+10};shop.nextBuy=now+1;L.Remote:Fire("StockShopSystem","Buy",shop.id,key,1);return
            end
        end;shop.nextBuy=now+2
    end
    local craftOptions={Aura={},Mount={}}
    local function halloweenRecipe(d,id)
        local terms={"halloween","pumpkin","spooky","ghost","candy"}
        local text=(tostring(d.Name or id).." "..tostring(id)):lower()
        for _,term in ipairs(terms) do if text:find(term,1,true) then return true end end
        for _,stage in pairs(d.Stages or {}) do
            for _,cost in ipairs(stage.Items or {}) do
                local info=itemData[cost.Id]
                local ingredient=(tostring(cost.Id).." "..tostring(info and info.Name or "")):lower()
                for _,term in ipairs(terms) do if ingredient:find(term,1,true) then return true end end
            end
        end
        return false
    end
    for id,d in pairs(upgrades or {}) do
        if type(d)=="table" and d.Stages and halloweenRecipe(d,id) then
            local label=tostring(d.Name or id);local search=(label.." "..id):lower()
            for kind in pairs(craftOptions) do if search:find(kind:lower(),1,true) then craftOptions[kind][#craftOptions[kind]+1]={Title=label,Value=id} end end
        end
    end
    sort(craftOptions.Aura);sort(craftOptions.Mount)
    tab:AddSection("Halloween Craft")
    local craft={Aura={ids={},on=false},Mount={ids={},on=false},cursor={Aura=1,Mount=1},retry={}}
    for kind in pairs(craftOptions) do local plural=kind=="Aura" and "Auras" or "Mounts"
        tab:AddDropdown({Title="Select "..plural,Multi=true,Default={},Options=craftOptions[kind],Callback=function(v)craft[kind].ids=v or {};craft.cursor[kind]=1 end})
        tab:AddToggle({Title="Auto Craft "..plural,Default=false,Description="Uses selected recipe requirements and available materials.",Callback=function(v)craft[kind].on=v end})
    end
    local function stepCraft(kind)
        local selected=craft[kind];if not selected.on or #selected.ids==0 then return end
        for _=1,#selected.ids do local id=selected.ids[craft.cursor[kind]];craft.cursor[kind]=craft.cursor[kind]%#selected.ids+1;local d=upgrades[id]
            if d and d.Stages and L:GetService("AutoService").CanUseUpgrade(L.PlayerData,id) then local level=L.PlayerData.Upgrades[id.."_Stage"] or 0;local stage=d.Stages[level+1];local enough=stage~=nil
                for _,item in ipairs(stage and stage.Items or {}) do if (tonumber(L.PlayerData.Items[item.Id]) or 0)<item.Amount then enough=false;break end end
                if enough and os.clock()>=(craft.retry[id] or 0) then craft.retry[id]=os.clock()+3;L.Remote:Fire("UpgradeSystem","Buy",id,"Stage");return end
            end
        end
    end
    task.spawn(function() self.setIdentity(2);while state.running do if self.window.ready then pcall(stepShop,os.clock());pcall(stepCraft,"Aura");pcall(stepCraft,"Mount") end;task.wait(0.5) end end)
end

function Runtime:buildModeShortcuts()
    local mirrors = {}
    for _, groupId in ipairs({ "raid", "portal", "trial", "invasion", "tower", "defense" }) do
        local page = self.uiGroups[groupId].Pages.Automation
        for _, entry in ipairs({ { "modeEquip", "Auto Equip Best" }, { "modeBoost", "Auto Use Boosts" } }) do
            local key, title = entry[1], entry[2]
            local master = self.state.controls[key]
            local control = page:AddToggle({
                Title = title,
                Default = master:Get(),
                Column = key == "modeBoost" and 2 or 1,
                Description = "Shared enable switch for mode automation. This mode uses its own selections below.",
                Flag = "layout." .. groupId .. "." .. key,
                Callback = function(value)
                    if self.window.restoring then
                        return
                    end
                    master:Set(value)
                    for _, mirror in ipairs(mirrors) do
                        if mirror.key == key then
                            mirror.control:Set(value, true)
                        end
                    end
                end,
            })
            mirrors[#mirrors + 1] = { key = key, control = control }
        end
    end
    task.spawn(function()
        while self.state.running do
            if self.window.ready then
                for _, mirror in ipairs(mirrors) do
                    local value = self.state.controls[mirror.key]:Get()
                    if mirror.control:Get() ~= value then
                        mirror.control:Set(value, true)
                    end
                end
            end
            task.wait(0.5)
        end
    end)
end

function Runtime:buildEventWebhook()
    local s, L, tab = self.state, self.Library, self.tabs.alerts
    self.setIdentity(2)
    local systems = L:GetService("InventoryService"):GetSystems()
    local catalogs = {}
    for kind, info in pairs(systems) do
        if type(info.Data) == "function" then
            local ok, result = pcall(info.Data)
            if ok and type(result) == "table" then
                catalogs[kind] = result
            end
        end
    end
    catalogs.Pet = L:GetData("PetData")
    catalogs.Item = L:GetData("ItemData")
    self.setIdentity(8)
    local settings = {
        url = "",
        events = {},
        pings = {},
        userId = "",
        queue = {},
        pending = {},
        previous = nil,
        nextReport = 0,
        sent = 0,
        version = 0,
        teleporting = false,
        disconnected = false,
    }
    s.eventWebhook = settings
    local options = {
        { Title = "Broken Hero Obtained", Value = "Broken" },
        { Title = "Disconnected", Value = "Disconnected" },
        { Title = "Inventory Update (every 30s)", Value = "Inventory" },
    }
    local known = { Broken = true, Disconnected = true, Inventory = true }
    local function reset()
        settings.version += 1
        table.clear(settings.queue)
        settings.pending = {}
        settings.previous = nil
        settings.nextReport = os.clock() + 30
    end
    local function set(values)
        local result = {}
        for _, v in ipairs(values or {}) do
            if known[v] then
                result[v] = true
            end
        end
        return result
    end
    tab:AddSection("Webhook Notifications")
    tab:AddParagraph({
        Title = "Your Discord notifications",
        Description = "Sends only the selected alerts to your URL. Includes Roblox username, new heroes and inventory gains; no IP or device data. Inventory reports are sent every 30 seconds, including when nothing changed. Disconnect delivery is best effort and cannot work after a crash or loss of internet.",
    })
    local input
    input = tab:AddInput({
        Title = "Discord Webhook URL",
        Default = "",
        Placeholder = "https://discord.com/api/webhooks/.../...",
        Callback = function(v)
            local url = EventAlerts.url(v)
            if url == nil then
                self.window:Notify({
                    Title = "Invalid webhook",
                    Description = "Paste the full Discord webhook URL, including its token.",
                    Duration = 5,
                })
                if input then
                    input:Set(settings.url, true)
                end
                return
            end
            if url ~= settings.url then
                reset()
                settings.error = nil
            end
            settings.url = url
            if input then
                input:Set(url, true)
            end
        end,
    })
    s.controls.eventWebhookUrl = input
    s.controls.eventWebhookEvents = tab:AddDropdown({
        Title = "Notifications to Send",
        Multi = true,
        Default = {},
        Options = options,
        Callback = function(values)
            settings.events = set(values)
            reset()
        end,
    })
    tab:AddSection("Discord Mentions")
    local user
    user = tab:AddInput({
        Title = "Discord User ID",
        Default = "",
        Placeholder = "Your Discord user ID (optional)",
        Callback = function(v)
            local id = WeatherAlerts.normalizeUser(v)
            if id == nil then
                self.window:Notify({
                    Title = "Invalid Discord ID",
                    Description = "Use your 17–20 digit Discord user ID, not your username.",
                    Duration = 5,
                })
                if user then
                    user:Set(settings.userId, true)
                end
                return
            end
            settings.userId = id
            if user then
                user:Set(id, true)
            end
        end,
    })
    s.controls.eventWebhookUser = user
    s.controls.eventWebhookPings = tab:AddDropdown({
        Title = "Notifications That Mention You",
        Multi = true,
        Default = {},
        Options = options,
        Description = "Only mentions you for enabled notifications selected here.",
        Callback = function(v)
            settings.pings = set(v)
        end,
    })
    local function enqueue(kind, description)
        if settings.url == "" or not settings.events[kind] then
            return
        end
        if #settings.queue >= 32 then
            settings.error = "Notification queue full; an alert was skipped."
            return
        end
        local entry = {
            kind = kind,
            description = description,
            url = settings.url,
            version = settings.version,
            attempts = 0,
            readyAt = 0,
            time = os.time(),
        }
        if kind == "Disconnected" then
            table.insert(settings.queue, 1, entry)
        else
            table.insert(settings.queue, entry)
        end
    end
    tab:AddButton({
        Title = "Webhook Status",
        Callback = function()
            self.window:Notify({
                Title = "Webhook",
                Description = settings.url == "" and "Add your webhook URL first."
                    or settings.error
                    or (settings.sent .. " sent; " .. #settings.queue .. " queued."),
                Duration = 5,
            })
        end,
    })
    task.spawn(function()
        self.setIdentity(2)
        while s.running do
            if self.window.ready and L.PlayerData then
                local ok = pcall(function()
                    if settings.url == "" or not next(settings.events) then
                        settings.previous = nil
                        return
                    end
                    if settings.events.Broken or settings.events.Inventory then
                        if type(L.PlayerData.Items) ~= "table" or type(L.PlayerData.Pets) ~= "table" then
                            return
                        end
                        local snapshot = EventAlerts.snapshot(L.PlayerData, systems, catalogs)
                        local hadBaseline = settings.previous ~= nil
                        local broken = EventAlerts.diff(settings.previous, snapshot, settings.pending)
                        settings.previous = snapshot
                        if not hadBaseline then
                            settings.nextReport = os.clock() + 30
                        end
                        if settings.events.Broken and next(broken) then
                            local summary = {}
                            for name, count in pairs(broken) do
                                summary[#summary + 1] = "+" .. count .. " " .. name .. " (Broken)"
                            end
                            table.sort(summary)
                            enqueue("Broken", table.concat(summary, "\n"))
                        end
                        if os.clock() >= settings.nextReport then
                            enqueue("Inventory", EventAlerts.lines(settings.pending))
                            settings.pending = {}
                            settings.nextReport = os.clock() + 30
                        end
                    end
                end)
                if not ok then
                    settings.error = "Unable to read inventory changes."
                end
            end
            task.wait(1)
        end
    end)
    task.spawn(function()
        self.setIdentity(8)
        local Http = game:GetService("HttpService")
        while s.running do
            local entry = settings.queue[1]
            if entry and os.clock() >= entry.readyAt then
                if
                    entry.url ~= settings.url
                    or entry.version ~= settings.version
                    or not settings.events[entry.kind]
                then
                    table.remove(settings.queue, 1)
                else
                    local send = request or http_request or (syn and syn.request) or (http and http.request)
                    if type(send) ~= "function" then
                        settings.error = "This executor does not support HTTP requests."
                        table.remove(settings.queue, 1)
                    else
                        entry.attempts += 1
                        local payload = EventAlerts.payload(
                            entry.kind,
                            entry.description,
                            settings.userId,
                            settings.pings[entry.kind],
                            self.player.Name,
                            entry.time
                        )
                        local ok, response = pcall(function()
                            return send({
                                Url = entry.url,
                                Method = "POST",
                                Headers = { ["Content-Type"] = "application/json" },
                                Body = Http:JSONEncode(payload),
                            })
                        end)
                        local status = ok and type(response) == "table" and tonumber(response.StatusCode)
                        if status and status >= 200 and status < 300 then
                            settings.sent += 1
                            settings.error = nil
                        elseif status == 429 and entry.attempts < 3 then
                            local delay = 5
                            local decoded, body = pcall(Http.JSONDecode, Http, response.Body or "")
                            if decoded and type(body) == "table" then
                                delay = tonumber(body.retry_after) or delay
                            end
                            entry.readyAt = os.clock() + math.clamp(delay, 1, 300)
                            settings.error = "Discord rate limit; waiting to retry."
                        else
                            settings.error = "Unable to deliver alert"
                                .. (status and (" (HTTP " .. status .. ").") or ".")
                        end
                        if entry.readyAt <= os.clock() or entry.attempts >= 3 then
                            local index = table.find(settings.queue, entry)
                            if index then
                                table.remove(settings.queue, index)
                            end
                        end
                    end
                end
            end
            task.wait(0.25)
        end
    end)
    local connections = {}
    local function disconnected()
        if not self.window.ready or not s.running or settings.teleporting or settings.disconnected then
            return
        end
        settings.disconnected = true
        enqueue(
            "Disconnected",
            "The client detected a lost connection or a disconnect screen. Delivery depends on the executor and internet connection remaining available."
        )
    end
    connections[#connections + 1] = self.player.OnTeleport:Connect(function(status)
        if status == Enum.TeleportState.Started or status == Enum.TeleportState.InProgress then
            settings.teleporting = true
        end
    end)
    connections[#connections + 1] = game:GetService("TeleportService").TeleportInitFailed:Connect(function(p)
        if p == self.player then
            settings.teleporting = false
        end
    end)
    connections[#connections + 1] = game:GetService("GuiService").ErrorMessageChanged
        :Connect(function(message)
            local text = tostring(message or ""):lower()
            if
                text:find("disconnect", 1, true)
                or text:find("desconect", 1, true)
                or text:find("lost connection", 1, true)
                or text:find("kicked", 1, true)
            then
                disconnected()
            end
        end)
    local network = game:GetService("NetworkClient")
    connections[#connections + 1] = network.ChildRemoved:Connect(function(child)
        if child:IsA("ClientReplicator") then
            disconnected()
        end
    end)
    self.window.Gui.Destroying:Connect(function()
        for _, connection in ipairs(connections) do
            connection:Disconnect()
        end
        table.clear(settings.queue)
    end)
end

function Runtime:buildLanguage()
    local tab = self.tabs.language
    tab:AddSection("Language")
    tab:AddParagraph({
        Title = "Interface Language",
        Description = "Choose the interface language. Changes apply immediately and are saved automatically.",
    })
    self.state.controls.uiLanguage = tab:AddDropdown({
        Title = "Interface Language",
        Flag = "tbl.interface.language",
        Default = "en",
        Multi = false,
        Options = {
            { Title = "English", Value = "en" },
            { Title = "Português (Brasil)", Value = "pt-BR" },
            { Title = "Português (Portugal)", Value = "pt-PT" },
            { Title = "Español", Value = "es" },
        },
        Callback = function(value)
            TBLanguage:setLocale(value)
        end,
    })
end

return Runtime.new()
