<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Canil Clicker</title>
<style>
*{box-sizing:border-box}body{font-family:'Segoe UI',Arial,sans-serif;margin:0;padding:10px;
    background: linear-gradient(135deg,#667eea 0%,#764ba2 100%),
                url('https://images.unsplash.com/photo-1548199973-03cce0bbc87b?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80');
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
    min-height:100vh
}.container{max-width:1200px;margin:0 auto}.game-header{background:#fff;border-radius:15px;padding:15px 20px;margin-bottom:15px;box-shadow:0 4px 12px rgba(0,0,0,0.1);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px}.stats-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:10px;flex-grow:1}.stat-box{background:#f8f9fa;padding:10px;border-radius:10px;border-left:4px solid #667eea}.stat-value{font-size:18px;font-weight:bold;color:#333}.stat-label{font-size:11px;color:#666;text-transform:uppercase;letter-spacing:.5px}.main-panel{background:#fff;border-radius:15px;margin-bottom:15px;box-shadow:0 4px 12px rgba(0,0,0,0.1);overflow:hidden}.tabs{display:flex;background:#f8f9fa;border-bottom:2px solid #e9ecef}.tab{padding:12px 20px;background:0;border:0;cursor:pointer;font-weight:500;color:#666;transition:all .3s;position:relative}.tab.active{color:#667eea;background:#fff}.tab.active::after{content:'';position:absolute;bottom:-2px;left:0;right:0;height:2px;background:#667eea}.tab-content{padding:20px;display:none}.tab-content.active{display:block}.items-grid,.dogs-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:15px}.dog-card,.item-card{background:#f8f9fa;padding:15px;border-radius:10px;border:1px solid #e9ecef;transition:transform .2s}.dog-card:hover,.item-card:hover{transform:translateY(-2px);box-shadow:0 4px 8px rgba(0,0,0,0.1)}.dog-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px}.dog-name{font-weight:bold;font-size:14px}.dog-breed{font-size:12px;color:#666;margin-bottom:5px}.progress-container{height:6px;background:#e9ecef;border-radius:3px;margin:5px 0;overflow:hidden}.progress-bar{height:100%;transition:width .3s}.btn{padding:8px 12px;border:0;border-radius:6px;cursor:pointer;font-weight:500;font-size:12px;transition:all .2s}.btn-primary{background:#667eea;color:#fff}.btn-primary:hover{background:#5a6fd8}.btn-success{background:#28a745;color:#fff}.btn-success:hover{background:#218838}.btn-warning{background:#ffc107;color:#333}.btn-warning:hover{background:#e0a800}.btn-danger{background:#dc3545;color:#fff}.btn-danger:hover{background:#c82333}.rebirth-card{background:linear-gradient(135deg,#fff3cd 0%,#ffeaa7 100%);border:2px solid #ffd700;padding:20px;border-radius:10px;text-align:center;margin-bottom:20px}.prestige-badge{display:inline-block;background:linear-gradient(45deg,#FFD700,#FFA500);color:#fff;padding:4px 12px;border-radius:20px;font-weight:bold;font-size:14px;margin-bottom:10px}.breeding-container{display:flex;gap:20px;flex-wrap:wrap;align-items:center;justify-content:center;margin-bottom:20px}.selected-dog{background:#fff;padding:15px;border-radius:10px;border:2px dashed #dee2e6;min-width:150px;text-align:center}.breeding-arrow{font-size:24px;color:#667eea}.event-modal,.modal-overlay{display:none;position:fixed}.event-modal{top:50%;left:50%;transform:translate(-50%,-50%);background:#fff;padding:20px;border-radius:15px;box-shadow:0 10px 30px rgba(0,0,0,0.3);z-index:1000;min-width:300px;text-align:center}.modal-overlay{top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,0.5);z-index:999}.quick-actions{display:flex;gap:10px;margin-bottom:15px;flex-wrap:wrap}
/* Estilos para o sistema de pontuação */
.points-badge {
    display: inline-block;
    background: linear-gradient(45deg, #6a11cb, #2575fc);
    color: #fff;
    padding: 4px 12px;
    border-radius: 20px;
    font-weight: bold;
    font-size: 14px;
    margin-left: 10px;
}
.rarity-indicator {
    font-size: 10px;
    padding: 2px 6px;
    border-radius: 10px;
    margin-left: 5px;
    font-weight: bold;
}
.rarity-common { background: #6c757d; color: white; }
.rarity-uncommon { background: #28a745; color: white; }
.rarity-rare { background: #007bff; color: white; }
.rarity-epic { background: #6f42c1; color: white; }
.rarity-legendary { background: #fd7e14; color: white; }

/* Estilos para o sistema de trabalho - ADICIONADO */
.task-system-container {
    margin-top: 20px;
}
.task-types {
    display: flex;
    gap: 10px;
    margin-bottom: 15px;
    flex-wrap: wrap;
}
.task-type-btn {
    flex: 1;
    min-width: 120px;
}
.task-card {
    background: #f8f9fa;
    border-radius: 10px;
    padding: 15px;
    margin-bottom: 10px;
    border-left: 4px solid #4CAF50;
}
.task-card.in-progress {
    border-left-color: #FF9800;
    background: #FFF3E0;
}
.task-card.completed {
    border-left-color: #4CAF50;
    background: #E8F5E9;
}
.task-info {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
}
.task-timer {
    font-size: 14px;
    font-weight: bold;
    color: #333;
}
.cooldown-timer {
    color: #F44336;
}
.task-reward {
    background: #E3F2FD;
    padding: 5px 10px;
    border-radius: 5px;
    font-size: 12px;
    color: #1976D2;
}
.task-dog-selector {
    margin-top: 10px;
    padding: 10px;
    background: #fff;
    border-radius: 5px;
    border: 1px solid #ddd;
}
.dog-option {
    display: flex;
    justify-content: space-between;
    padding: 5px;
    margin-bottom: 5px;
    background: #f5f5f5;
    border-radius: 3px;
    cursor: pointer;
    transition: background 0.2s;
}
.dog-option:hover {
    background: #e0e0e0;
}
.dog-option.selected {
    background: #C8E6C9;
    border: 1px solid #4CAF50;
}
.dog-option.disabled {
    opacity: 0.5;
    cursor: not-allowed;
}
.dog-status {
    font-size: 10px;
    padding: 2px 6px;
    border-radius: 10px;
    font-weight: bold;
}
.status-working { background: #FF9800; color: white; }
.status-available { background: #4CAF50; color: white; }

/* Estilos para o display de chances */
#chancesDisplay {
    transition: all 0.3s ease;
    position: fixed;
    bottom: 10px;
    right: 10px;
    background: rgba(255, 255, 255, 0.95);
    padding: 10px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.2);
    font-size: 11px;
    z-index: 999;
    max-width: 250px;
    border: 1px solid #ddd;
}

#chancesDisplay:hover {
    transform: scale(1.05);
    box-shadow: 0 4px 20px rgba(0,0,0,0.3);
}

/* Novos estilos para botões especiais */
.special-button {
    margin-top: 10px;
    padding: 10px;
    background: linear-gradient(45deg, #FF9800, #FF5722);
    color: white;
    border: none;
    border-radius: 8px;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s;
    width: 100%;
}

.special-button:hover:not(:disabled) {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}

.special-button:disabled {
    opacity: 0.6;
    cursor: not-allowed;
}

.special-button.cooldown {
    background: linear-gradient(45deg, #757575, #9e9e9e);
}

/* Estilos para informações de bônus ativos */
.active-bonus-indicator {
    background: linear-gradient(45deg, #4CAF50, #8BC34A);
    color: white;
    padding: 5px 10px;
    border-radius: 20px;
    font-size: 12px;
    font-weight: bold;
    display: inline-block;
    margin-top: 5px;
}

.active-bonus-indicator.water {
    background: linear-gradient(45deg, #2196F3, #03A9F4);
}
</style>
</head>
<body>
<div class="container">
  <div class="game-header">
    <div style="flex-shrink:0">
      <h1 style="margin:0;font-size:24px;color:#333">🐕 Canil Clicker <span class="points-badge" id="totalPointsBadge">Pontos: 0</span></h1>
      <div class="prestige-badge" id="headerPrestige">Prestígio: 0</div>
    </div>
    <div class="stats-grid">
      <div class="stat-box"><div class="stat-label">Moedas</div><div class="stat-value" id="headerMoedas">0.00</div></div>
      <div class="stat-box"><div class="stat-label">Renda/s</div><div class="stat-value" id="headerRenda">0.00</div></div>
      <div class="stat-box"><div class="stat-label">Cães</div><div class="stat-value" id="headerCaes">0/2</div></div>
      <div class="stat-box"><div class="stat-label">Comida/Água</div><div class="stat-value" id="headerRecursos">0.0/0.0</div></div>
    </div>
    <button class="btn btn-warning" onclick="mostrarTab('rebirth', this)" id="rebirthBtnHeader">🔄 Rebirth</button>
  </div>
  <div class="quick-actions">
    <button class="btn btn-primary" onclick="moedas+=1;atualizarUI();criarEfeitoMoeda(event)">✨ Acariciar (+1 moeda)</button>
    <button class="btn btn-success" id="comprarCaoBtn">🐕 Comprar Cão (200)</button>
    <button class="btn" style="background:#6c757d;color:#fff" id="buyFoodBtn">🍖 Comprar Comida (1:1)</button>
  </div>
  <div class="main-panel">
    <div class="tabs">
      <button class="tab active" onclick="mostrarTab('canil', this)">🏠 Canil</button>
      <button class="tab" onclick="mostrarTab('caes', this)">🐶 Cães</button>
      <button class="tab" onclick="mostrarTab('trabalho', this)">💼 Trabalho</button>
      <button class="tab" onclick="mostrarTab('breeding', this)">❤️ Breeding</button>
      <button class="tab" onclick="mostrarTab('rebirth', this)">🔄 Rebirth</button>
      <button class="tab" onclick="mostrarTab('pontuacao', this)">🏆 Pontos</button>
    </div>
    <div class="tab-content active" id="tab-canil">
      <div class="items-grid">
        <div class="item-card"><h4 style="margin:0 0 10px">🏠 Casinha</h4><div>Nível: <span id="casinhaLvl">0</span>/5</div><div class="progress-container"><div class="progress-bar" id="casinhaProgress" style="width:0%;background:#4caf50"></div></div><button class="btn btn-primary" id="buildCasinhaBtn" style="margin-top:10px;width:100%">Construir (200)</button><button class="btn btn-success" id="upgradeCasinhaBtn" style="margin-top:5px;width:100%" disabled>Upgrade (---)</button></div>
        <div class="item-card"><h4 style="margin:0 0 10px">🍽️ Comedouro</h4><div>Nível: <span id="comedouroLvl">0</span>/5</div><div>Gera: <span id="comedouroGera">0.0</span>/s comida</div><button class="btn btn-primary" id="buildComedouroBtn" style="margin-top:10px;width:100%">Construir (500)</button><button class="btn btn-success" id="upgradeComedouroBtn" style="margin-top:5px;width:100%" disabled>Upgrade (---)</button></div>
        <div class="item-card"><h4 style="margin:0 0 10px">💧 Bebedouro</h4><div>Nível: <span id="bebedouroLvl">0</span>/5</div><div>Gera: <span id="bebedouroGera">0.0</span>/s água</div><button class="btn btn-primary" id="buildBebedouroBtn" style="margin-top:10px;width:100%">Construir (500)</button><button class="btn btn-success" id="upgradeBebedouroBtn" style="margin-top:5px;width:100%" disabled>Upgrade (---)</button></div>
        
        <!-- 🎾 Brinquedo - MODIFICADO -->
        <div class="item-card" id="brinquedoCard">
            <h4 style="margin:0 0 10px">🎾 Brinquedo</h4>
            <div>Nível: <span id="brinquedoLvl">0</span>/5</div>
            <div>Benefício: +<span id="brinquedoRenda">0.00</span>/s renda</div>
            <div id="brinquedoUpgradeInfo" style="font-size:12px;color:#666;margin:5px 0">
                Próximo upgrade: <span id="brinquedoUpgradeCost">100 comida, 100 água</span>
            </div>
            <button class="btn btn-primary" id="buildBrinquedoBtn" style="margin-top:10px;width:100%">Construir (500)</button>
            <button class="btn btn-success" id="upgradeBrinquedoBtn" style="margin-top:5px;width:100%" disabled>Upgrade</button>
            <div id="doubleExpSection" style="display:none;margin-top:10px;">
                <button class="special-button" id="doubleExpBtn" onclick="ativarDoubleExp()">🎯 ATIVAR DOUBLE EXP</button>
                <div id="doubleExpCooldown" style="font-size:11px;color:#666;margin-top:5px;text-align:center"></div>
            </div>
        </div>
        
        <!-- ⚽ Atividade - MODIFICADO -->
        <div class="item-card" id="atividadeCard">
            <h4 style="margin:0 0 10px">⚽ Atividade</h4>
            <div>Nível: <span id="atividadeLvl">0</span>/5</div>
            <div>Benefício: +<span id="atividadeRenda">0.00</span>/s renda</div>
            <div id="atividadeUpgradeInfo" style="font-size:12px;color:#666;margin:5px 0">
                Próximo upgrade: <span id="atividadeUpgradeCost">100 água</span>
            </div>
            <button class="btn btn-primary" id="buildAtividadeBtn" style="margin-top:10px;width:100%">Construir (500)</button>
            <button class="btn btn-success" id="upgradeAtividadeBtn" style="margin-top:5px;width:100%" disabled>Upgrade</button>
            <div id="hidratacaoSection" style="display:none;margin-top:10px;">
                <button class="special-button" id="hidratacaoBtn" onclick="ativarHidratacao()">💧 ATIVAR HIDRATAÇÃO</button>
                <div id="hidratacaoCooldown" style="font-size:11px;color:#666;margin-top:5px;text-align:center"></div>
            </div>
        </div>
        
        <div class="item-card"><h4 style="margin:0 0 10px">🏥 Clínica</h4><div>Nível: <span id="clinicaLvl">0</span>/5</div><button class="btn btn-primary" id="buildClinicaBtn" style="margin-top:10px;width:100%">Construir (500)</button><button class="btn btn-success" id="upgradeClinicaBtn" style="margin-top:5px;width:100%" disabled>Upgrade (---)</button></div>
      </div>
      
      <!-- Seção de bônus ativos -->
      <div id="activeBonusesSection" style="margin-top:20px;background:#f8f9fa;padding:15px;border-radius:10px;display:none">
          <h4 style="margin:0 0 10px">🎁 Bônus Ativos</h4>
          <div id="activeBonusesList">
              <!-- Bônus ativos serão mostrados aqui -->
          </div>
      </div>
    </div>
    
    <!-- Restante do código permanece igual -->
    <div class="tab-content" id="tab-caes"><div id="dogsList"><div style="text-align:center;padding:20px;color:#666">Nenhum cão ainda. Compre seu primeiro cão!</div></div></div>
    
    <!-- ABA DE TRABALHO -->
    <div class="tab-content" id="tab-trabalho">
      <div class="task-system-container">
        <h3 style="margin-top:0;color:#333">💼 Sistema de Trabalho e Atividades</h3>
        <p style="color:#666;margin-bottom:15px">Envie seus cães para trabalhos e atividades para ganhar EXP. Cada cão só pode fazer uma tarefa por vez.</p>
        
        <!-- Indicador de Double EXP ativo -->
        <div id="doubleExpActiveIndicator" style="display:none;background:linear-gradient(45deg,#FF9800,#FF5722);color:white;padding:10px;border-radius:8px;margin-bottom:15px;text-align:center">
            🎯 DOUBLE EXP ATIVO! Todas as tarefas dão o dobro de EXP! (<span id="doubleExpTimer"></span>)
        </div>
        
        <div class="task-types">
          <button class="btn btn-primary task-type-btn" onclick="mostrarTarefas('trabalho')">🏢 Trabalhos</button>
          <button class="btn btn-success task-type-btn" onclick="mostrarTarefas('atividade')">⚽ Atividades</button>
        </div>
        
        <div id="tasksContainer">
          <!-- As tarefas serão carregadas dinamicamente aqui -->
        </div>
        
        <div id="selectedTaskDetails" style="display:none;">
          <div class="task-card" id="taskDetailCard">
            <div class="task-info">
              <div>
                <h4 style="margin:0" id="taskDetailTitle">Título da Tarefa</h4>
                <div id="taskDetailDesc">Descrição da tarefa</div>
              </div>
              <div class="task-timer" id="taskDetailTimer">--:--</div>
            </div>
            <div class="task-reward">Recompensa: <span id="taskDetailReward">0 EXP</span></div>
            
            <div class="task-dog-selector" id="taskDogSelector">
              <h5 style="margin:0 0 10px 0">Selecione um cão:</h5>
              <div id="dogSelectionList">
                <!-- Lista de cães será carregada aqui -->
              </div>
            </div>
            
            <div style="display:flex;gap:10px;margin-top:10px">
              <button class="btn btn-success" id="startTaskBtn" onclick="iniciarTarefa()">Iniciar Tarefa</button>
              <button class="btn" style="background:#6c757d;color:#fff" onclick="cancelarSelecaoTarefa()">Cancelar</button>
            </div>
          </div>
        </div>
        
        <div id="activeTasksContainer">
          <!-- Tarefas ativas serão mostradas aqui -->
        </div>
      </div>
    </div>
    
    <!-- Restante do código (breeding, rebirth, pontuacao) permanece igual -->
    <div class="tab-content" id="tab-breeding">
      <div class="breeding-container">
        <div class="selected-dog"><div style="font-size:12px;color:#666;margin-bottom:5px">Cão 1</div><div id="selectedDog1" style="font-weight:bold;color:#667eea">---</div><div id="selectedDog1Info" style="font-size:11px;color:#999"></div></div>
        <div class="breeding-arrow">❤️ → 🐕 →</div>
        <div class="selected-dog"><div style="font-size:12px;color:#666;margin-bottom:5px">Cão 2</div><div id="selectedDog2" style="font-weight:bold;color:#e91e63">---</div><div id="selectedDog2Info" style="font-size:11px;color:#999"></div></div>
      </div>
      <div style="text-align:center;margin:20px 0"><div style="background:#f8f9fa;padding:15px;border-radius:10px;display:inline-block"><div>Chance de sucesso: <span id="breedingChance" style="font-weight:bold">0%</span></div><div>Custo: <span id="breedingCost" style="font-weight:bold">0</span> moedas</div></div></div>
      <div style="text-align:center"><button class="btn btn-danger" id="startBreedingBtn" style="padding:12px 30px;font-size:16px" disabled>🐾 INICIAR CRUZAMENTO</button><button class="btn" style="background:#6c757d;color:#fff;margin-left:10px" id="clearSelectionBtn">Limpar Seleção</button></div>
      <div id="breedingResult" style="margin-top:20px"></div>
    </div>
    <div class="tab-content" id="tab-rebirth">
      <div class="rebirth-card">
        <div class="prestige-badge">Prestígio Atual: <span id="currentPrestige">0</span></div>
        <h3 style="margin:10px 0;color:#333">🔄 Sistema Rebirth</h3>
        <div style="background:#fff;padding:15px;border-radius:8px;margin:15px 0">
          <div style="font-size:14px;color:#666">Próximo rebirth requer:</div>
          <div style="font-size:24px;font-weight:bold;color:#FFD700" id="rebirthRequirement">10,000 moedas</div>
          <div style="margin:10px 0"><div class="progress-container" style="height:10px"><div class="progress-bar" id="rebirthProgressBar" style="background:#FFD700;width:0%"></div></div><div style="font-size:12px;color:#666;text-align:center;margin-top:5px" id="rebirthProgressText">Progresso: 0%</div></div>
        </div>
        <button class="btn btn-warning" id="rebirthBtn" style="padding:12px 30px;font-size:16px;font-weight:bold" disabled>🔄 FAZER REBIRTH</button>
        <div style="margin-top:20px;text-align:left;background:rgba(255,255,255,0.8);padding:15px;border-radius:8px"><h4 style="margin:0 0 10px">🎁 Bônus Atuais:</h4><div>✅ +<span id="currentIncomeBonus">0</span>% renda passiva</div><div>✅ +<span id="currentCapacityBonus">0</span> capacidade de cães</div><div>✅ +<span id="currentResourceBonus">0</span>% comida/água gerada</div></div>
      </div>
    </div>
    <div class="tab-content" id="tab-pontuacao">
      <div style="background:linear-gradient(135deg,#6a11cb 0%,#2575fc 100%);border-radius:10px;padding:20px;color:white;margin-bottom:20px;text-align:center">
        <h2 style="margin:0 0 10px 0">🏆 Sistema de Pontuação</h2>
        <div style="font-size:24px;font-weight:bold;margin:10px 0">Pontuação Total: <span id="pontuacaoTotal">0</span></div>
        <div style="display:flex;justify-content:space-around;margin-top:15px;flex-wrap:wrap;gap:10px">
          <div style="background:rgba(255,255,255,0.2);padding:10px;border-radius:8px;min-width:150px">
            <div style="font-size:12px;opacity:0.9">Pontos por Rebirths</div>
            <div style="font-size:18px;font-weight:bold" id="pontosRebirths">0</div>
          </div>
          <div style="background:rgba(255,255,255,0.2);padding:10px;border-radius:8px;min-width:150px">
            <div style="font-size:12px;opacity:0.9">Pontos por Cães</div>
            <div style="font-size:18px;font-weight:bold" id="pontosCaes">0</div>
          </div>
          <div style="background:rgba(255,255,255,0.2);padding:10px;border-radius:8px;min-width:150px">
            <div style="font-size:12px;opacity:0.9">Multiplicador</div>
            <div style="font-size:18px;font-weight:bold" id="multiplicadorPontos">1x</div>
          </div>
        </div>
      </div>
      
      <div style="background:#fff;border-radius:10px;padding:20px;margin-bottom:15px">
        <h3 style="margin-top:0;color:#333">📊 Como Ganhar Pontos</h3>
        <div style="display:grid;grid-template-columns:repeat(auto-fit, minmax(250px, 1fr));gap:15px;margin-top:15px">
          <div style="border-left:4px solid #6a11cb;padding-left:10px">
            <h4 style="margin:0 0 5px 0;color:#6a11cb">🔄 Por Rebirths</h4>
            <p style="margin:0;font-size:14px;color:#666">Cada rebirth: <strong>100 pontos × Prestígio</strong></p>
            <p style="margin:5px 0 0 0;font-size:12px;color:#999">Ex: Prestígio 5 = 500 pontos</p>
          </div>
          <div style="border-left:4px solid #28a745;padding-left:10px">
            <h4 style="margin:0 0 5px 0;color:#28a745">🐕 Por Cães Raros</h4>
            <p style="margin:0;font-size:14px;color:#666">Pontos baseados na raridade da raça</p>
            <p style="margin:5px 0 0 0;font-size:12px;color:#999">+ bônus por traços especiais</p>
          </div>
          <div style="border-left:4px solid #ffc107;padding-left:10px">
            <h4 style="margin:0 0 5px 0;color:#ffc107">⭐ Multiplicador</h4>
            <p style="margin:0;font-size:14px;color:#666">Seus pontos totais são multiplicados por:</p>
            <p style="margin:5px 0 0 0;font-size:12px;color:#999">(Prestígio + 1)</p>
          </div>
        </div>
      </div>
      
      <div style="background:#fff;border-radius:10px;padding:20px">
        <h3 style="margin-top:0;color:#333">🎯 Tabela de Raridade</h3>
        <div style="display:grid;grid-template-columns:repeat(auto-fit, minmax(200px, 1fr));gap:10px;margin-top:10px">
          <div style="background:#f8f9fa;padding:10px;border-radius:8px;border-left:4px solid #6c757d">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <span>Vira-lata</span>
              <span class="rarity-indicator rarity-common">Comum</span>
            </div>
            <div style="font-size:18px;font-weight:bold;color:#333;text-align:right">10 pts</div>
          </div>
          <div style="background:#f8f9fa;padding:10px;border-radius:8px;border-left:4px solid #28a745">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <span>Poodle</span>
              <span class="rarity-indicator rarity-uncommon">Incomum</span>
            </div>
            <div style="font-size:18px;font-weight:bold;color:#333;text-align:right">25 pts</div>
          </div>
          <div style="background:#f8f9fa;padding:10px;border-radius:8px;border-left:4px solid #007bff">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <span>Pastor Alemão</span>
              <span class="rarity-indicator rarity-rare">Raro</span>
            </div>
            <div style="font-size:18px;font-weight:bold;color:#333;text-align:right">50 pts</div>
          </div>
          <div style="background:#f8f9fa;padding:10px;border-radius:8px;border-left:4px solid #6f42c1">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <span>Golden Retriever</span>
              <span class="rarity-indicator rarity-epic">Épico</span>
            </div>
            <div style="font-size:18px;font-weight:bold;color:#333;text-align:right">100 pts</div>
          </div>
          <div style="background:#f8f9fa;padding:10px;border-radius:8px;border-left:4px solid #fd7e14">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <span>Husky Siberiano</span>
              <span class="rarity-indicator rarity-legendary">Lendário</span>
            </div>
            <div style="font-size:18px;font-weight:bold;color:#333;text-align:right">250 pts</div>
          </div>
        </div>
        <div style="margin-top:15px;padding:10px;background:#f8f9fa;border-radius:8px">
          <p style="margin:0;font-size:12px;color:#666">⚠️ <strong>Nota:</strong> Cães criados via breeding dão 25% mais pontos! Traços especiais (Inteligente, Fértil, Brincalhão) dão +5 pontos cada.</p>
        </div>
      </div>
    </div>
  </div>
</div>
<div class="modal-overlay" id="eventOverlay"></div>
<div class="event-modal" id="lixoModal"><h3>🗑️ Lixo Encontrado!</h3><p>Clique para limpar e ganhar recompensas!</p><button class="btn btn-warning" onclick="coletarLixo()" style="padding:10px 20px;font-size:16px">Limpar Lixo (+20 moedas +5 EXP)</button></div>
<div class="event-modal" id="pulgaModal"><h3>🦠 Pulgas Atacaram!</h3><p>Clique para eliminar e ganhar recompensas!</p><button class="btn btn-danger" onclick="coletarPulga()" style="padding:10px 20px;font-size:16px">Eliminar Pulgas (+10 moedas +10 EXP)</button></div>

<script>
// ============================================
// VARIÁVEIS GLOBAIS
// ============================================
let prestigeLevel = 0;
let rebirthBonus = {incomeMultiplier: 0, resourceMultiplier: 0, extraCapacity: 0};
let moedas = 0;
let food = 0;
let agua = 0;
let rendaPassivaBase = 0.01;
let rendaAdicional = 0;
let rendaTotal = 0; // CORRIGIDO: Apenas uma declaração

// Níveis dos edifícios
let casinhaLevel = 0;
let bebedouroLevel = 0;
let comedouroLevel = 0;
let brinquedoLevel = 0;
let atividadeLevel = 0;
let clinicaLevel = 0;

// Novas variáveis para os sistemas especiais
let doubleExpActive = false;
let doubleExpEndTime = 0;
let doubleExpCooldownEndTime = 0;
let hidratacaoActive = false;
let hidratacaoEndTime = 0;
let hidratacaoCooldownEndTime = 0;

// Custo de upgrade para brinquedo e atividade
const brinquedoUpgradeCosts = [
    { food: 0, agua: 0 }, // nível 0 (não existe)
    { food: 100, agua: 100 }, // nível 1
    { food: 200, agua: 200 }, // nível 2
    { food: 300, agua: 300 }, // nível 3
    { food: 400, agua: 400 }, // nível 4
    { food: 500, agua: 500 }  // nível 5
];

const atividadeUpgradeCosts = [
    { agua: 0 }, // nível 0 (não existe)
    { agua: 100 }, // nível 1
    { agua: 200 }, // nível 2
    { agua: 300 }, // nível 3
    { agua: 400 }, // nível 4
    { agua: 500 }  // nível 5
];

let upgradeCosts = [0, 1000, 2000, 3000, 4000, 5000];
let genders = ['M', 'F'];
let breeds = [
    {name: "Vira-lata", baseIncome: 0.1, color: "#8B4513"},
    {name: "Poodle", baseIncome: 0.15, color: "#FFFFFF"},
    {name: "Pastor Alemão", baseIncome: 0.2, color: "#000000"},
    {name: "Golden Retriever", baseIncome: 0.25, color: "#FFD700"},
    {name: "Husky Siberiano", baseIncome: 0.3, color: "#E0FFFF"}
];

// NOVO SISTEMA DE TRAÇOS
let traits = [
    {name: "Fértil", breedBonus: 0.02},        // +2% chance no breeding
    {name: "Brincalhão", foodBonus: 0.05},     // +0.05 comida/s
    {name: "Trabalhador", expBonus: 0.05},     // +5% EXP
    {name: "Rico", coinBonus: 0.1},           // +0.1 moedas/s
    {name: "Poseidon", waterBonus: 0.1}       // +0.1 água/s
];

// Probabilidades para cães recém-nascidos
const traitProbabilities = {
    "Fértil": 30,      // 30%
    "Brincalhão": 20,   // 20%
    "Trabalhador": 20,  // 20%
    "Rico": 10,         // 10%
    "Poseidon": 10,     // 10%
    null: 10           // 10% sem traço
};

// Traços que dão pontos extras
const pointTraits = ["Fértil", "Brincalhão", "Trabalhador", "Rico", "Poseidon"];

let dogs = [];
let foodConsumptionPerDog = 0.1;
let selectedDogs = [];
let breedingCost = 500;
let cooldownTrabalho = 0;
let cooldownAtividade = 0;

// Variáveis do sistema de pontuação
let totalPoints = 0;
let pointsFromRebirths = 0;
let pointsFromDogs = 0;
let prestigeMultiplier = 1;

// Sistema de raridade para pontuação
const breedRarityPoints = {
    "Vira-lata": { points: 10, rarity: "common" },
    "Poodle": { points: 25, rarity: "uncommon" },
    "Pastor Alemão": { points: 50, rarity: "rare" },
    "Golden Retriever": { points: 100, rarity: "epic" },
    "Husky Siberiano": { points: 250, rarity: "legendary" }
};

// ============================================
// SISTEMA DE SACRIFÍCIO
// ============================================
let sacrificeCount = 0;
let sacrificeCost = 1000;
let sacrificeCostMultiplier = 1.5;
let temporaryIncomeBonus = 0;
let temporaryIncomeBonusEndTime = 0;

// ============================================
// SISTEMA DE TRABALHO/ATIVIDADE
// ============================================
let activeTasks = [];
let selectedTaskType = null;
let selectedTaskIndex = null;
let selectedDogForTask = null;

const tasks = {
    trabalho: [
        {
            id: 1,
            name: "Guarda Noturno",
            description: "Proteger o território durante a noite",
            duration: 180,
            baseExp: 25,
            cooldown: 300,
            icon: "🌙",
            requires: { level: 1 }
        },
        {
            id: 2,
            name: "Pastoreio",
            description: "Ajudar com ovelhas na fazenda",
            duration: 300,
            baseExp: 40,
            cooldown: 600,
            icon: "🐑",
            requires: { level: 3 }
        },
        {
            id: 3,
            name: "Busca e Resgate",
            description: "Treinamento de busca e salvamento",
            duration: 600,
            baseExp: 75,
            cooldown: 1200,
            icon: "🚨",
            requires: { level: 5 }
        },
        {
            id: 4,
            name: "Terapia Animal",
            description: "Visitar hospital para terapia",
            duration: 450,
            baseExp: 60,
            cooldown: 900,
            icon: "❤️",
            requires: { level: 4 }
        }
    ],
    atividade: [
        {
            id: 5,
            name: "Corrida no Parque",
            description: "Exercício físico e diversão",
            duration: 120,
            baseExp: 15,
            cooldown: 240,
            icon: "🏃",
            requires: { level: 1 }
        },
        {
            id: 6,
            name: "Agility Training",
            description: "Treino de obstáculos e agilidade",
            duration: 180,
            baseExp: 30,
            cooldown: 360,
            icon: "🎯",
            requires: { level: 2 }
        },
        {
            id: 7,
            name: "Natação",
            description: "Exercício na piscina",
            duration: 240,
            baseExp: 35,
            cooldown: 480,
            icon: "🏊",
            requires: { level: 3 }
        },
        {
            id: 8,
            name: "Competição de Frisbee",
            description: "Competição de agilidade com frisbee",
            duration: 300,
            baseExp: 50,
            cooldown: 600,
            icon: "🥏",
            requires: { level: 4 }
        }
    ]
};

// ============================================
// NOVO SISTEMA DE COMPRA DE CÃES
// ============================================
let comprasDeCaes = 0; // Contador de quantos cães foram comprados
let precoBaseCao = 200; // Preço base do cão
let multiplicadorPreco = 1.1; // Multiplicador de preço por compra

// Sistema de raridade com probabilidades baseadas em pontos
const breedRarityWeights = {
    "Vira-lata": { baseWeight: 50, minPoints: 0 },
    "Poodle": { baseWeight: 30, minPoints: 100 },
    "Pastor Alemão": { baseWeight: 15, minPoints: 500 },
    "Golden Retriever": { baseWeight: 4, minPoints: 2000 },
    "Husky Siberiano": { baseWeight: 1, minPoints: 5000 }
};

// ============================================
// NOVAS FUNÇÕES PARA BRINQUEDO E ATIVIDADE
// ============================================

function getBrinquedoUpgradeCost(level) {
    if (level >= 5) return null;
    return brinquedoUpgradeCosts[level + 1];
}

function getAtividadeUpgradeCost(level) {
    if (level >= 5) return null;
    return atividadeUpgradeCosts[level + 1];
}

function upgradeBrinquedo() {
    if (brinquedoLevel === 0) {
        alert("Primeiro você precisa construir o Brinquedo!");
        return;
    }
    
    if (brinquedoLevel >= 5) {
        alert("Brinquedo já está no nível máximo!");
        return;
    }
    
    const cost = getBrinquedoUpgradeCost(brinquedoLevel);
    if (!cost) return;
    
    if (food < cost.food) {
        alert(`Comida insuficiente! Você precisa de ${cost.food} comida.`);
        return;
    }
    
    if (agua < cost.agua) {
        alert(`Água insuficiente! Você precisa de ${cost.agua} água.`);
        return;
    }
    
    // Deduzir recursos
    food -= cost.food;
    agua -= cost.agua;
    brinquedoLevel++;
    
    // Atualizar UI
    atualizarUI();
    
    // Mostrar mensagem
    alert(`🎾 Brinquedo atualizado para nível ${brinquedoLevel}!\n` +
          `Gasto: ${cost.food} comida e ${cost.agua} água\n` +
          `Bônus: +${(brinquedoLevel * 0.05).toFixed(2)}/s de renda`);
    
    // Salvar jogo
    salvarJogo();
}

function upgradeAtividade() {
    if (atividadeLevel === 0) {
        alert("Primeiro você precisa construir a Área de Atividade!");
        return;
    }
    
    if (atividadeLevel >= 5) {
        alert("Atividade já está no nível máximo!");
        return;
    }
    
    const cost = getAtividadeUpgradeCost(atividadeLevel);
    if (!cost) return;
    
    if (agua < cost.agua) {
        alert(`Água insuficiente! Você precisa de ${cost.agua} água.`);
        return;
    }
    
    // Deduzir recurso
    agua -= cost.agua;
    atividadeLevel++;
    
    // Atualizar UI
    atualizarUI();
    
    // Mostrar mensagem
    alert(`⚽ Atividade atualizada para nível ${atividadeLevel}!\n` +
          `Gasto: ${cost.agua} água\n` +
          `Bônus: +${(atividadeLevel * 0.05).toFixed(2)}/s de renda`);
    
    // Salvar jogo
    salvarJogo();
}

function ativarDoubleExp() {
    // Verificar se já está ativo
    if (doubleExpActive) {
        alert("Double EXP já está ativo!");
        return;
    }
    
    // Verificar se está em cooldown
    const now = Date.now();
    if (now < doubleExpCooldownEndTime) {
        const remaining = Math.ceil((doubleExpCooldownEndTime - now) / 1000);
        const minutes = Math.floor(remaining / 60);
        const seconds = remaining % 60;
        alert(`Double EXP está em cooldown! Aguarde ${minutes}:${seconds.toString().padStart(2, '0')}`);
        return;
    }
    
    // Verificar recursos
    if (moedas < 1000) {
        alert("Moedas insuficientes! Você precisa de 1000 moedas.");
        return;
    }
    
    if (food < 250) {
        alert("Comida insuficiente! Você precisa de 250 comida.");
        return;
    }
    
    if (agua < 100) {
        alert("Água insuficiente! Você precisa de 100 água.");
        return;
    }
    
    // Confirmar
    if (!confirm("Ativar Double EXP por 1 hora?\n\nCusto:\n• 1000 moedas\n• 250 comida\n• 100 água\n\nCooldown: 2 horas")) {
        return;
    }
    
    // Deduzir recursos
    moedas -= 1000;
    food -= 250;
    agua -= 100;
    
    // Ativar bônus
    doubleExpActive = true;
    doubleExpEndTime = now + (60 * 60 * 1000); // 1 hora
    doubleExpCooldownEndTime = now + (2 * 60 * 60 * 1000); // 2 horas de cooldown
    
    // Atualizar UI
    atualizarUI();
    
    // Mostrar mensagem
    alert("🎯 DOUBLE EXP ATIVADO!\n\nTodas as tarefas darão o DOBRO de EXP por 1 hora!\n\nCooldown de 2 horas após o término.");
    
    // Salvar jogo
    salvarJogo();
}

function ativarHidratacao() {
    // Verificar se já está ativo
    if (hidratacaoActive) {
        alert("Hidratação já está ativa!");
        return;
    }
    
    // Verificar se está em cooldown
    const now = Date.now();
    if (now < hidratacaoCooldownEndTime) {
        const remaining = Math.ceil((hidratacaoCooldownEndTime - now) / 1000);
        const minutes = Math.floor(remaining / 60);
        const seconds = remaining % 60;
        alert(`Hidratação está em cooldown! Aguarde ${minutes}:${seconds.toString().padStart(2, '0')}`);
        return;
    }
    
    // Verificar recursos
    if (moedas < 1000) {
        alert("Moedas insuficientes! Você precisa de 1000 moedas.");
        return;
    }
    
    if (food < 250) {
        alert("Comida insuficiente! Você precisa de 250 comida.");
        return;
    }
    
    // Confirmar
    if (!confirm("Ativar Hidratação por 1 hora?\n\nCusto:\n• 1000 moedas\n• 250 comida\n\nBenefício: DOBRO de água gerada por segundo\nCooldown: 2 horas")) {
        return;
    }
    
    // Deduzir recursos
    moedas -= 1000;
    food -= 250;
    
    // Ativar bônus
    hidratacaoActive = true;
    hidratacaoEndTime = now + (60 * 60 * 1000); // 1 hora
    hidratacaoCooldownEndTime = now + (2 * 60 * 60 * 1000); // 2 horas de cooldown
    
    // Atualizar UI
    atualizarUI();
    
    // Mostrar mensagem
    alert("💧 HIDRATAÇÃO ATIVADA!\n\nVocê gerará o DOBRO de água por segundo por 1 hora!\n\nCooldown de 2 horas após o término.");
    
    // Salvar jogo
    salvarJogo();
}

function updateBonusTimers() {
    const now = Date.now();
    
    // Atualizar Double EXP
    if (doubleExpActive && now >= doubleExpEndTime) {
        doubleExpActive = false;
        alert("⏰ Double EXP terminou!");
    }
    
    // Atualizar Hidratação
    if (hidratacaoActive && now >= hidratacaoEndTime) {
        hidratacaoActive = false;
        alert("⏰ Hidratação terminou!");
    }
    
    // Atualizar UI dos botões
    updateBrinquedoUI();
    updateAtividadeUI();
    updateActiveBonusesUI();
}

function updateBrinquedoUI() {
    const now = Date.now();
    const doubleExpSection = document.getElementById("doubleExpSection");
    const doubleExpBtn = document.getElementById("doubleExpBtn");
    const doubleExpCooldown = document.getElementById("doubleExpCooldown");
    
    if (brinquedoLevel >= 5) {
        doubleExpSection.style.display = "block";
        
        if (doubleExpActive) {
            // Bônus ativo
            const remaining = Math.ceil((doubleExpEndTime - now) / 1000);
            const minutes = Math.floor(remaining / 60);
            const seconds = remaining % 60;
            doubleExpBtn.disabled = true;
            doubleExpBtn.textContent = "🎯 DOUBLE EXP ATIVO";
            doubleExpBtn.classList.add("cooldown");
            doubleExpCooldown.innerHTML = `⏰ Termina em: ${minutes}:${seconds.toString().padStart(2, '0')}`;
        } else if (now < doubleExpCooldownEndTime) {
            // Em cooldown
            const remaining = Math.ceil((doubleExpCooldownEndTime - now) / 1000);
            const minutes = Math.floor(remaining / 60);
            const seconds = remaining % 60;
            doubleExpBtn.disabled = true;
            doubleExpBtn.textContent = "🎯 EM COOLDOWN";
            doubleExpBtn.classList.add("cooldown");
            doubleExpCooldown.innerHTML = `⏰ Disponível em: ${minutes}:${seconds.toString().padStart(2, '0')}`;
        } else {
            // Disponível
            doubleExpBtn.disabled = false;
            doubleExpBtn.textContent = "🎯 ATIVAR DOUBLE EXP";
            doubleExpBtn.classList.remove("cooldown");
            doubleExpCooldown.innerHTML = "Custo: 1000 moedas, 250 comida, 100 água<br>Duração: 1 hora • Cooldown: 2 horas";
        }
    } else {
        doubleExpSection.style.display = "none";
    }
}

function updateAtividadeUI() {
    const now = Date.now();
    const hidratacaoSection = document.getElementById("hidratacaoSection");
    const hidratacaoBtn = document.getElementById("hidratacaoBtn");
    const hidratacaoCooldown = document.getElementById("hidratacaoCooldown");
    
    if (atividadeLevel >= 5) {
        hidratacaoSection.style.display = "block";
        
        if (hidratacaoActive) {
            // Bônus ativo
            const remaining = Math.ceil((hidratacaoEndTime - now) / 1000);
            const minutes = Math.floor(remaining / 60);
            const seconds = remaining % 60;
            hidratacaoBtn.disabled = true;
            hidratacaoBtn.textContent = "💧 HIDRATAÇÃO ATIVA";
            hidratacaoBtn.classList.add("cooldown");
            hidratacaoCooldown.innerHTML = `⏰ Termina em: ${minutes}:${seconds.toString().padStart(2, '0')}`;
        } else if (now < hidratacaoCooldownEndTime) {
            // Em cooldown
            const remaining = Math.ceil((hidratacaoCooldownEndTime - now) / 1000);
            const minutes = Math.floor(remaining / 60);
            const seconds = remaining % 60;
            hidratacaoBtn.disabled = true;
            hidratacaoBtn.textContent = "💧 EM COOLDOWN";
            hidratacaoBtn.classList.add("cooldown");
            hidratacaoCooldown.innerHTML = `⏰ Disponível em: ${minutes}:${seconds.toString().padStart(2, '0')}`;
        } else {
            // Disponível
            hidratacaoBtn.disabled = false;
            hidratacaoBtn.textContent = "💧 ATIVAR HIDRATAÇÃO";
            hidratacaoBtn.classList.remove("cooldown");
            hidratacaoCooldown.innerHTML = "Custo: 1000 moedas, 250 comida<br>Duração: 1 hora • Cooldown: 2 horas";
        }
    } else {
        hidratacaoSection.style.display = "none";
    }
}

function updateActiveBonusesUI() {
    const now = Date.now();
    const activeBonusesSection = document.getElementById("activeBonusesSection");
    const activeBonusesList = document.getElementById("activeBonusesList");
    const doubleExpActiveIndicator = document.getElementById("doubleExpActiveIndicator");
    
    let html = "";
    let hasActiveBonuses = false;
    
    // Double EXP
    if (doubleExpActive) {
        hasActiveBonuses = true;
        const remaining = Math.ceil((doubleExpEndTime - now) / 1000);
        const minutes = Math.floor(remaining / 60);
        const seconds = remaining % 60;
        html += `<div class="active-bonus-indicator">🎯 Double EXP: ${minutes}:${seconds.toString().padStart(2, '0')}</div>`;
        
        // Atualizar indicador na aba de trabalho
        if (doubleExpActiveIndicator) {
            doubleExpActiveIndicator.style.display = "block";
            document.getElementById("doubleExpTimer").textContent = `${minutes}:${seconds.toString().padStart(2, '0')}`;
        }
    } else {
        if (doubleExpActiveIndicator) {
            doubleExpActiveIndicator.style.display = "none";
        }
    }
    
    // Hidratação
    if (hidratacaoActive) {
        hasActiveBonuses = true;
        const remaining = Math.ceil((hidratacaoEndTime - now) / 1000);
        const minutes = Math.floor(remaining / 60);
        const seconds = remaining % 60;
        html += `<div class="active-bonus-indicator water">💧 Hidratação: ${minutes}:${seconds.toString().padStart(2, '0')}</div>`;
    }
    
    // Bônus de renda temporário (do sacrifício)
    if (temporaryIncomeBonus > 0 && now < temporaryIncomeBonusEndTime) {
        hasActiveBonuses = true;
        const remaining = Math.ceil((temporaryIncomeBonusEndTime - now) / 1000);
        const minutes = Math.floor(remaining / 60);
        const seconds = remaining % 60;
        html += `<div class="active-bonus-indicator" style="background:linear-gradient(45deg,#FF416C,#FF4B2B)">💰 +${temporaryIncomeBonus}% Renda: ${minutes}:${seconds.toString().padStart(2, '0')}</div>`;
    }
    
    if (hasActiveBonuses) {
        activeBonusesSection.style.display = "block";
        activeBonusesList.innerHTML = html;
    } else {
        activeBonusesSection.style.display = "none";
    }
}

// ============================================
// FUNÇÕES DO NOVO SISTEMA DE TRAÇOS
// ============================================

function getRandomTrait() {
    const rand = Math.random() * 100;
    let accumulated = 0;
    
    for (const [traitName, probability] of Object.entries(traitProbabilities)) {
        accumulated += probability;
        if (rand <= accumulated) {
            if (traitName === "null") return null;
            return traits.find(t => t.name === traitName);
        }
    }
    return null;
}

function inheritTraits(parent1, parent2) {
    const inheritedTraits = [];
    
    // Herda traço do pai 1 (50% de chance)
    if (parent1.traits && parent1.traits.length > 0 && Math.random() < 0.5) {
        const trait1 = parent1.traits[Math.floor(Math.random() * parent1.traits.length)];
        if (trait1 && canAddTrait(inheritedTraits, trait1)) {
            inheritedTraits.push(trait1);
        }
    }
    
    // Herda traço do pai 2 (50% de chance)
    if (parent2.traits && parent2.traits.length > 0 && Math.random() < 0.5) {
        const trait2 = parent2.traits[Math.floor(Math.random() * parent2.traits.length)];
        if (trait2 && canAddTrait(inheritedTraits, trait2)) {
            inheritedTraits.push(trait2);
        }
    }
    
    // Adiciona traço aleatório se não herdou nenhum (10% de chance)
    if (inheritedTraits.length === 0 && Math.random() < 0.1) {
        const newTrait = getRandomTrait();
        if (newTrait && canAddTrait(inheritedTraits, newTrait)) {
            inheritedTraits.push(newTrait);
        }
    }
    
    // Limita a 4 traços no máximo
    return inheritedTraits.slice(0, 4);
}

function canAddTrait(existingTraits, newTrait) {
    if (!newTrait) return false;
    
    // Verifica se já tem este traço
    const hasTrait = existingTraits.some(t => t.name === newTrait.name);
    if (hasTrait) return false;
    
    // Verifica limite de 4 traços
    if (existingTraits.length >= 4) return false;
    
    return true;
}

function applyTraitEffects(dog, effects) {
    let modifiedEffects = {...effects};
    
    if (dog.traits && dog.traits.length > 0) {
        dog.traits.forEach(trait => {
            switch(trait.name) {
                case "Brincalhão":
                    modifiedEffects.foodGeneration += trait.foodBonus || 0.05;
                    break;
                case "Trabalhador":
                    modifiedEffects.expMultiplier *= (1 + (trait.expBonus || 0.05));
                    break;
                case "Rico":
                    modifiedEffects.incomeBonus += trait.coinBonus || 0.1;
                    break;
                case "Poseidon":
                    modifiedEffects.waterGeneration += trait.waterBonus || 0.1;
                    break;
                // Fértil é aplicado separadamente no breeding
            }
        });
    }
    
    return modifiedEffects;
}

// ============================================
// SISTEMA DE SACRIFÍCIO
// ============================================

function canSacrifice() {
    return clinicaLevel >= 5;
}

function getCurrentSacrificeCost() {
    return Math.floor(sacrificeCost * Math.pow(sacrificeCostMultiplier, sacrificeCount));
}

function sacrificarCao(dogIndex) {
    if (!canSacrifice()) {
        alert("Você precisa ter a Clínica no nível 5 para poder sacrificar cães!");
        return;
    }
    
    const dog = dogs[dogIndex];
    if (!dog || !dog.alive) {
        alert("Este cão não existe ou já está morto!");
        return;
    }
    
    const aliveDogs = dogs.filter(d => d.alive);
    if (aliveDogs.length <= 1) {
        alert("Você precisa ter pelo menos 1 cão vivo para poder sacrificar outro!");
        return;
    }
    
    const currentCost = getCurrentSacrificeCost();
    const nomeCao = dog.name || `Cão ${dogIndex + 1}`;
    
    const confirmMessage = `Tem certeza que deseja sacrificar ${nomeCao}?\n\n` +
                          `🎯 Cão: ${dog.breed} (Nível ${dog.level})\n` +
                          `💰 Custo: ${currentCost} moedas\n` +
                          `🎁 Recompensas:\n` +
                          `   • +${Math.floor(currentCost * 0.5)} moedas\n` +
                          `   • +${Math.floor(calculateDogPoints(dog) * 0.75)} pontos\n` +
                          `   • +5% de renda por 60 segundos\n\n` +
                          `⚠️ Esta ação é permanente! ${nomeCao} será removido do jogo.`;
    
    if (!confirm(confirmMessage)) return;
    
    if (moedas < currentCost) {
        alert(`Moedas insuficientes! Você precisa de ${currentCost} moedas.`);
        return;
    }
    
    moedas -= currentCost;
    const rewardCoins = Math.floor(currentCost * 0.5);
    const rewardPoints = Math.floor(calculateDogPoints(dog) * 0.75);
    
    moedas += rewardCoins;
    addTemporaryIncomeBonus(5, 60);
    sacrificeCount++;
    
    dogs[dogIndex].alive = false;
    dogs[dogIndex].deathReason = "sacrificed";
    
    updatePointsSystem();
    atualizarUI();
    renderDogsList();
    
    alert(`⚰️ SACRIFÍCIO REALIZADO!\n\n` +
          `Você sacrificou ${nomeCao} (${dog.breed} - Nível ${dog.level}).\n\n` +
          `🎁 Recompensas recebidas:\n` +
          `• +${rewardCoins} moedas\n` +
          `• +${rewardPoints} pontos\n` +
          `• +5% de renda por 60 segundos\n\n` +
          `💰 Próximo sacrifício custará: ${getCurrentSacrificeCost()} moedas`);
    
    salvarJogo();
}

function addTemporaryIncomeBonus(percent, durationSeconds) {
    temporaryIncomeBonus = percent;
    temporaryIncomeBonusEndTime = Date.now() + (durationSeconds * 1000);
    updateActiveBonusesUI();
}

function updateTemporaryBonusUI() {
    const now = Date.now();
    const remainingTime = Math.max(0, temporaryIncomeBonusEndTime - now);
    
    if (remainingTime > 0) {
        let bonusIndicator = document.getElementById("temporaryBonusIndicator");
        if (!bonusIndicator) {
            bonusIndicator = document.createElement("div");
            bonusIndicator.id = "temporaryBonusIndicator";
            bonusIndicator.style.position = "fixed";
            bonusIndicator.style.top = "10px";
            bonusIndicator.style.right = "10px";
            bonusIndicator.style.background = "linear-gradient(45deg, #FF416C, #FF4B2B)";
            bonusIndicator.style.color = "white";
            bonusIndicator.style.padding = "5px 10px";
            bonusIndicator.style.borderRadius = "5px";
            bonusIndicator.style.fontSize = "12px";
            bonusIndicator.style.fontWeight = "bold";
            bonusIndicator.style.zIndex = "1000";
            bonusIndicator.style.boxShadow = "0 2px 10px rgba(0,0,0,0.3)";
            document.body.appendChild(bonusIndicator);
        }
        
        const minutes = Math.floor(remainingTime / 60000);
        const seconds = Math.floor((remainingTime % 60000) / 1000);
        bonusIndicator.textContent = `🎁 +${temporaryIncomeBonus}% renda (${minutes}:${seconds.toString().padStart(2, '0')})`;
    } else {
        temporaryIncomeBonus = 0;
        const bonusIndicator = document.getElementById("temporaryBonusIndicator");
        if (bonusIndicator) bonusIndicator.remove();
    }
}

// ============================================
// FUNÇÕES DO SISTEMA DE PONTUAÇÃO
// ============================================

function calculateDogPoints(dog) {
    let points = 0;
    const breedInfo = breedRarityPoints[dog.breed] || { points: 10, rarity: "common" };
    points += breedInfo.points;
    
    if (dog.parents && dog.parents.length === 2) {
        points = Math.floor(points * 1.25);
    }
    
    if (dog.traits) {
        dog.traits.forEach(trait => {
            if (pointTraits.includes(trait.name)) points += 5;
        });
    }
    
    points += dog.level;
    return points;
}

function updatePointsSystem() {
    pointsFromRebirths = prestigeLevel * 100;
    pointsFromDogs = 0;
    dogs.forEach(dog => {
        if (dog.alive) pointsFromDogs += calculateDogPoints(dog);
    });
    
    prestigeMultiplier = prestigeLevel + 1;
    totalPoints = (pointsFromRebirths + pointsFromDogs) * prestigeMultiplier;
    updatePointsUI();
}

function updatePointsUI() {
    document.getElementById("totalPointsBadge").textContent = `Pontos: ${totalPoints}`;
    if (document.getElementById("pontuacaoTotal")) {
        document.getElementById("pontuacaoTotal").textContent = totalPoints;
        document.getElementById("pontosRebirths").textContent = pointsFromRebirths;
        document.getElementById("pontosCaes").textContent = pointsFromDogs;
        document.getElementById("multiplicadorPontos").textContent = `${prestigeMultiplier}x`;
    }
    updateDogCardsRarity();
}

function updateDogCardsRarity() {
    const dogCards = document.querySelectorAll('.dog-card');
    dogs.forEach((dog, index) => {
        if (dogCards[index]) {
            const breedInfo = breedRarityPoints[dog.breed] || { points: 10, rarity: "common" };
            const breedElement = dogCards[index].querySelector('.dog-breed');
            const oldIndicator = breedElement.querySelector('.rarity-indicator');
            if (oldIndicator) oldIndicator.remove();
            
            const raritySpan = document.createElement('span');
            raritySpan.className = `rarity-indicator rarity-${breedInfo.rarity}`;
            raritySpan.textContent = breedInfo.rarity.charAt(0).toUpperCase() + breedInfo.rarity.slice(1);
            breedElement.appendChild(raritySpan);
        }
    });
}

// ============================================
// FUNÇÕES DO SISTEMA DE TRABALHO
// ============================================

function mostrarTarefas(tipo) {
    selectedTaskType = tipo;
    selectedTaskIndex = null;
    selectedDogForTask = null;
    
    const container = document.getElementById("tasksContainer");
    const tituloTipo = tipo === 'trabalho' ? '🏢 Trabalhos Disponíveis' : '⚽ Atividades Disponíveis';
    
    let html = `<h4 style="margin-top:0">${tituloTipo}</h4>`;
    
    tasks[tipo].forEach((task, index) => {
        const podeRealizar = true;
        html += `
        <div class="task-card ${!podeRealizar ? 'disabled' : ''}" onclick="${podeRealizar ? `selecionarTarefa('${tipo}', ${index})` : ''}" style="cursor:${podeRealizar ? 'pointer' : 'not-allowed'}">
            <div class="task-info">
                <div>
                    <h5 style="margin:0">${task.icon} ${task.name}</h5>
                    <div style="font-size:12px;color:#666">${task.description}</div>
                </div>
                <div style="text-align:right">
                    <div style="font-size:14px;font-weight:bold">${formatarTempo(task.duration)}</div>
                    <div style="font-size:12px;color:#666">${task.baseExp} EXP</div>
                </div>
            </div>
            <div class="task-reward">Requer nível ${task.requires.level}+ • Cooldown: ${formatarTempo(task.cooldown)}</div>
        </div>
        `;
    });
    
    container.innerHTML = html;
    document.getElementById("selectedTaskDetails").style.display = "none";
    atualizarTarefasAtivas();
}

function selecionarTarefa(tipo, index) {
    selectedTaskType = tipo;
    selectedTaskIndex = index;
    selectedDogForTask = null;
    
    const task = tasks[tipo][index];
    const detailContainer = document.getElementById("selectedTaskDetails");
    
    document.getElementById("taskDetailTitle").innerHTML = `${task.icon} ${task.name}`;
    document.getElementById("taskDetailDesc").textContent = task.description;
    
    // Aplicar bônus de Double EXP se estiver ativo
    let expReward = task.baseExp;
    if (doubleExpActive) {
        expReward *= 2;
    }
    
    document.getElementById("taskDetailReward").textContent = `${expReward} EXP${doubleExpActive ? ' (Double EXP!)' : ''}`;
    document.getElementById("taskDetailTimer").textContent = formatarTempo(task.duration);
    
    carregarCaesParaTarefa();
    detailContainer.style.display = "block";
    document.getElementById("tasksContainer").style.display = "none";
    detailContainer.scrollIntoView({ behavior: 'smooth', block: 'start' });
}

function carregarCaesParaTarefa() {
    const task = tasks[selectedTaskType][selectedTaskIndex];
    const container = document.getElementById("dogSelectionList");
    
    let html = "";
    
    dogs.forEach((dog, index) => {
        if (!dog.alive) return;
        
        const estaTrabalhando = activeTasks.some(task => task.dogIndex === index && !task.completed);
        const podeParticipar = !estaTrabalhando && dog.level >= task.requires.level;
        const nomeCao = dog.name || `Cão ${index + 1}`;
        
        html += `
        <div class="dog-option ${podeParticipar ? '' : 'disabled'} ${selectedDogForTask === index ? 'selected' : ''}" 
             onclick="${podeParticipar ? `selecionarCaoParaTarefa(${index})` : ''}">
            <div>
                <strong>${nomeCao}</strong> - ${dog.breed}
                <div style="font-size:11px;color:#666">Nível ${dog.level} • ${dog.gender === 'M' ? '♂' : '♀'}</div>
            </div>
            <div>
                <span class="dog-status ${estaTrabalhando ? 'status-working' : 'status-available'}">
                    ${estaTrabalhando ? 'TRABALHANDO' : 'DISPONÍVEL'}
                </span>
            </div>
        </div>
        `;
    });
    
    if (html === "") {
        html = '<div style="text-align:center;padding:10px;color:#666">Nenhum cão disponível para esta tarefa.</div>';
        document.getElementById("startTaskBtn").disabled = true;
    } else {
        document.getElementById("startTaskBtn").disabled = selectedDogForTask === null;
    }
    
    container.innerHTML = html;
}

function selecionarCaoParaTarefa(dogIndex) {
    selectedDogForTask = dogIndex;
    carregarCaesParaTarefa();
    document.getElementById("startTaskBtn").disabled = false;
}

function iniciarTarefa() {
    if (selectedTaskType === null || selectedTaskIndex === null || selectedDogForTask === null) {
        alert("Selecione uma tarefa e um cão primeiro!");
        return;
    }
    
    const task = tasks[selectedTaskType][selectedTaskIndex];
    const dog = dogs[selectedDogForTask];
    const estaTrabalhando = activeTasks.some(t => t.dogIndex === selectedDogForTask && !t.completed);
    
    if (estaTrabalhando) {
        alert("Este cão já está realizando uma tarefa!");
        return;
    }
    
    if (dog.level < task.requires.level) {
        alert(`Este cão precisa estar no nível ${task.requires.level} para esta tarefa!`);
        return;
    }
    
    let expReward = task.baseExp;
    
    // Aplica bônus de Double EXP
    if (doubleExpActive) {
        expReward *= 2;
    }
    
    // Aplica bônus de traço Trabalhador
    if (dog.traits) {
        dog.traits.forEach(trait => {
            if (trait.name === "Trabalhador") {
                expReward = Math.floor(expReward * (1 + trait.expBonus));
            }
        });
    }
    
    expReward += Math.floor(dog.level * 0.5);
    
    const newTask = {
        id: Date.now(),
        taskType: selectedTaskType,
        taskIndex: selectedTaskIndex,
        dogIndex: selectedDogForTask,
        startTime: Date.now(),
        duration: task.duration * 1000,
        expReward: expReward,
        completed: false,
        claimable: false
    };
    
    activeTasks.push(newTask);
    salvarTarefasAtivas();
    cancelarSelecaoTarefa();
    atualizarTarefasAtivas();
    renderDogsList();
    
    const nomeCao = dog.name || `Cão ${selectedDogForTask + 1}`;
    alert(`🎯 ${nomeCao} (${dog.breed}) começou a tarefa "${task.name}"!\nRecompensa: ${expReward} EXP${doubleExpActive ? ' (Double EXP!)' : ''}\nTempo: ${formatarTempo(task.duration)}`);
}

function cancelarSelecaoTarefa() {
    // Não limpe selectedTaskType, apenas o índice
    selectedTaskIndex = null;
    selectedDogForTask = null;
    document.getElementById("selectedTaskDetails").style.display = "none";
    document.getElementById("tasksContainer").style.display = "block";
    // Sempre mostra as tarefas do tipo selecionado
    if (selectedTaskType) mostrarTarefas(selectedTaskType);
}

function atualizarTarefasAtivas() {
    const container = document.getElementById("activeTasksContainer");
    const tarefasAtivas = activeTasks.filter(task => !task.completed);
    
    if (tarefasAtivas.length === 0) {
        container.innerHTML = '<div style="text-align:center;padding:20px;color:#666">Nenhuma tarefa em andamento. Selecione uma tarefa acima!</div>';
        return;
    }
    
    let html = '<h4 style="margin-top:20px">🎯 Tarefas em Andamento</h4>';
    
    tarefasAtivas.forEach(task => {
        const taskInfo = tasks[task.taskType][task.taskIndex];
        const dog = dogs[task.dogIndex];
        const elapsed = Date.now() - task.startTime;
        const remaining = Math.max(0, task.duration - elapsed);
        const progress = Math.min(100, (elapsed / task.duration) * 100);
        const nomeCao = dog.name || `Cão ${task.dogIndex + 1}`;
        
        html += `
        <div class="task-card in-progress">
            <div class="task-info">
                <div>
                    <h5 style="margin:0">${taskInfo.icon} ${taskInfo.name}</h5>
                    <div style="font-size:12px;color:#666">${nomeCao} - ${dog.breed}</div>
                </div>
                <div class="task-timer">${formatarTempo(remaining / 1000)}</div>
            </div>
            <div class="progress-container" style="margin:10px 0">
                <div class="progress-bar" style="width:${progress}%;background:#4CAF50"></div>
            </div>
            <div style="display:flex;justify-content:space-between;align-items:center">
                <div class="task-reward">${task.expReward} EXP${doubleExpActive ? ' (Double EXP!)' : ''}</div>
                <button class="btn btn-primary" onclick="reclamarTarefa(${task.id})" ${task.claimable ? '' : 'disabled'} style="padding:5px 10px;font-size:12px">
                    ${task.claimable ? '🎁 Reclamar' : '⏳ Aguardando...'}
                </button>
            </div>
        </div>
        `;
    });
    
    container.innerHTML = html;
}

function reclamarTarefa(taskId) {
    const taskIndex = activeTasks.findIndex(t => t.id === taskId);
    if (taskIndex === -1) {
        alert("Tarefa não encontrada!");
        return;
    }
    
    const task = activeTasks[taskIndex];
    const dog = dogs[task.dogIndex];
    
    if (!task.claimable) {
        alert("A tarefa ainda não foi concluída!");
        return;
    }
    
    ganharExp(task.dogIndex, task.expReward);
    activeTasks[taskIndex].completed = true;
    salvarTarefasAtivas();
    atualizarTarefasAtivas();
    atualizarUI();
    
    const nomeCao = dog.name || `Cão ${task.dogIndex + 1}`;
    alert(`🎉 ${nomeCao} completou a tarefa e ganhou ${task.expReward} EXP!`);
}

function verificarTarefasCompletas() {
    const now = Date.now();
    let atualizarNecessario = false;
    
    activeTasks.forEach(task => {
        if (!task.completed) {
            const elapsed = now - task.startTime;
            if (elapsed >= task.duration && !task.claimable) {
                task.claimable = true;
                atualizarNecessario = true;
                
                if (document.getElementById("tab-trabalho").classList.contains("active")) {
                    const taskInfo = tasks[task.taskType][task.taskIndex];
                    const dog = dogs[task.dogIndex];
                    const nomeCao = dog.name || `Cão ${task.dogIndex + 1}`;
                    criarNotificacaoTarefa(`🎉 ${nomeCao} completou "${taskInfo.name}"! Clique para reclamar ${task.expReward} EXP.`);
                }
            }
        }
    });
    
    if (atualizarNecessario) {
        atualizarTarefasAtivas();
        salvarTarefasAtivas();
    }
}

function criarNotificacaoTarefa(mensagem) {
    const notificacao = document.createElement("div");
    notificacao.textContent = mensagem;
    notificacao.style.position = "fixed";
    notificacao.style.top = "20px";
    notificacao.style.right = "20px";
    notificacao.style.background = "#4CAF50";
    notificacao.style.color = "white";
    notificacao.style.padding = "10px 15px";
    notificacao.style.borderRadius = "5px";
    notificacao.style.boxShadow = "0 2px 10px rgba(0,0,0,0.2)";
    notificacao.style.zIndex = "10000";
    notificacao.style.cursor = "pointer";
    notificacao.style.fontSize = "14px";
    
    notificacao.onclick = function() {
        document.body.removeChild(notificacao);
        mostrarTab('trabalho', document.querySelector('.tab[onclick*="trabalho"]'));
    };
    
    document.body.appendChild(notificacao);
    
    setTimeout(() => {
        if (document.body.contains(notificacao)) {
            document.body.removeChild(notificacao);
        }
    }, 5000);
}

function salvarTarefasAtivas() {
    try {
        localStorage.setItem("canilClickerTasks", JSON.stringify(activeTasks));
    } catch (e) {
        console.error("Erro ao salvar tarefas:", e);
    }
}

function carregarTarefasAtivas() {
    try {
        const savedTasks = localStorage.getItem("canilClickerTasks");
        if (savedTasks) {
            activeTasks = JSON.parse(savedTasks);
            const now = Date.now();
            activeTasks.forEach(task => {
                if (!task.completed) {
                    const elapsed = now - task.startTime;
                    if (elapsed >= task.duration) task.claimable = true;
                }
            });
            salvarTarefasAtivas();
        }
    } catch (e) {
        console.error("Erro ao carregar tarefas:", e);
        activeTasks = [];
    }
}

function formatarTempo(segundos) {
    const minutos = Math.floor(segundos / 60);
    const segs = Math.floor(segundos % 60);
    return `${minutos.toString().padStart(2, '0')}:${segs.toString().padStart(2, '0')}`;
}

// ============================================
// FUNÇÕES PRINCIPAIS DO JOGO
// ============================================

// CORREÇÃO: Função mostrarTab atualizada
function mostrarTab(e, clickedElement) {
    document.querySelectorAll(".tab-content").forEach(t => t.classList.remove("active"));
    document.querySelectorAll(".tab").forEach(t => t.classList.remove("active"));
    document.getElementById(`tab-${e}`).classList.add("active");
    if (clickedElement) clickedElement.classList.add("active");
    if ("caes" === e) renderDogsList();
    if ("trabalho" === e) {
        if (!selectedTaskType) mostrarTarefas('trabalho');
        else mostrarTarefas(selectedTaskType);
    }
}

function atualizarHeader() {
    document.getElementById("headerMoedas").textContent = moedas.toFixed(2);
    document.getElementById("headerRenda").textContent = rendaTotal.toFixed(2);
    document.getElementById("headerCaes").textContent = `${dogs.filter(e => e.alive).length}/${getDogCapacity()}`;
    document.getElementById("headerRecursos").textContent = `${food.toFixed(1)}/${agua.toFixed(1)}`;
    document.getElementById("headerPrestige").textContent = `Prestígio: ${prestigeLevel}`;
}

function atualizarUI() {
    atualizarHeader();
    
    // Atualizar preço do botão de compra de cão
    document.getElementById("comprarCaoBtn").textContent = `🐕 Comprar Cão (${getCurrentDogPrice()})`;
    
    // Atualizar informações dos edifícios
    for (const e of ["casinha", "bebedouro", "comedouro", "clinica"]) {
        const t = eval(`${e}Level`);
        document.getElementById(`${e}Lvl`).textContent = t;
        if ("casinha" === e) {
            document.getElementById("casinhaProgress").style.width = `${t / 5 * 100}%`;
        }
        if ("comedouro" === e) {
            document.getElementById("comedouroGera").textContent = (.1 * t * (1 + rebirthBonus.resourceMultiplier / 100)).toFixed(1);
        }
        if ("bebedouro" === e) {
            document.getElementById("bebedouroGera").textContent = (.1 * t * (1 + rebirthBonus.resourceMultiplier / 100)).toFixed(1);
        }
    }
    
    // Atualizar brinquedo
    document.getElementById("brinquedoLvl").textContent = brinquedoLevel;
    document.getElementById("brinquedoRenda").textContent = (brinquedoLevel * 0.05).toFixed(2);
    const brinquedoCost = getBrinquedoUpgradeCost(brinquedoLevel);
    if (brinquedoCost) {
        document.getElementById("brinquedoUpgradeCost").textContent = `${brinquedoCost.food} comida, ${brinquedoCost.agua} água`;
        document.getElementById("upgradeBrinquedoBtn").disabled = false;
        document.getElementById("upgradeBrinquedoBtn").textContent = `Upgrade (${brinquedoCost.food} comida, ${brinquedoCost.agua} água)`;
    } else {
        document.getElementById("brinquedoUpgradeCost").textContent = "Nível máximo";
        document.getElementById("upgradeBrinquedoBtn").disabled = true;
        document.getElementById("upgradeBrinquedoBtn").textContent = "Nível MAX";
    }
    
    // Atualizar atividade
    document.getElementById("atividadeLvl").textContent = atividadeLevel;
    document.getElementById("atividadeRenda").textContent = (atividadeLevel * 0.05).toFixed(2);
    const atividadeCost = getAtividadeUpgradeCost(atividadeLevel);
    if (atividadeCost) {
        document.getElementById("atividadeUpgradeCost").textContent = `${atividadeCost.agua} água`;
        document.getElementById("upgradeAtividadeBtn").disabled = false;
        document.getElementById("upgradeAtividadeBtn").textContent = `Upgrade (${atividadeCost.agua} água)`;
    } else {
        document.getElementById("atividadeUpgradeCost").textContent = "Nível máximo";
        document.getElementById("upgradeAtividadeBtn").disabled = true;
        document.getElementById("upgradeAtividadeBtn").textContent = "Nível MAX";
    }
    
    // Atualizar botões de upgrade dos outros edifícios
    updateUpgradeButtonLabel("casinha", casinhaLevel);
    updateUpgradeButtonLabel("bebedouro", bebedouroLevel);
    updateUpgradeButtonLabel("comedouro", comedouroLevel);
    updateUpgradeButtonLabel("clinica", clinicaLevel);
    
    // Atualizar sistemas de bônus
    updateBonusTimers();
    updateBrinquedoUI();
    updateAtividadeUI();
    
    atualizarRebirthUI();
    atualizarSelecaoBreeding();
    atualizarRenda();
    updatePointsSystem();
    updateActiveBonusesUI();
    
    // Atualizar display de chances
    if (typeof updateChancesDisplay === 'function') {
        updateChancesDisplay();
    }
}

function atualizarRenda() {
    let e = 0;
    e += casinhaLevel * .05;
    e += bebedouroLevel * .05;
    e += comedouroLevel * .05;
    e += brinquedoLevel * .05; // Bônus do brinquedo
    e += atividadeLevel * .05; // Bônus da atividade
    e += clinicaLevel * .05;
    
    for (const t of dogs) {
        if (t.alive && t.hunger > 25) {
            let a = t.baseIncome || .1;
            
            // Aplica bônus de traço Rico
            if (t.traits) {
                t.traits.forEach(trait => {
                    if (trait.name === "Rico") {
                        a += trait.coinBonus || 0.1;
                    }
                });
            }
            
            a *= 1 + rebirthBonus.incomeMultiplier / 100;
            
            if (temporaryIncomeBonus > 0) {
                a *= (1 + temporaryIncomeBonus / 100);
            }
            
            e += a;
        }
    }
    
    rendaAdicional = e;
    rendaTotal = rendaPassivaBase + rendaAdicional; // CORRIGIDO: Somente aqui calcula rendaTotal
}

function renderDogsList() {
    const e = document.getElementById("dogsList");
    if (0 === dogs.length) {
        e.innerHTML = '<div style="text-align:center;padding:20px;color:#666">Nenhum cão ainda. Compre seu primeiro cão!</div>';
        return;
    }
    
    let t = '<div class="dogs-grid">';
    dogs.forEach((a, o) => {
        if (!a.alive) return;
        
        let i = a.baseIncome || .1;
        
        // Aplica bônus de traço Rico
        if (a.traits) {
            a.traits.forEach(trait => {
                if (trait.name === "Rico") {
                    i += trait.coinBonus || 0.1;
                }
            });
        }
        
        i *= 1 + rebirthBonus.incomeMultiplier / 100;
        
        const estaTrabalhando = activeTasks.some(task => task.dogIndex === o && !task.completed);
        const dogPoints = calculateDogPoints(a);
        const l = selectedDogs.includes(o);
        const podeSacrificar = canSacrifice() && dogs.filter(d => d.alive).length > 1;
        const nomeCao = a.name || `Cão ${o + 1}`;
        
        t += `
        <div class="dog-card" style="border-left:4px solid ${a.breedColor || "#8B4513"}">
            <div class="dog-header">
                <div class="dog-name">${nomeCao} ${estaTrabalhando ? '⏳' : ''} ${!a.customName ? '✏️' : ''}</div>
                <div style="font-size:11px;background:#6a11cb;color:white;padding:2px 6px;border-radius:10px;font-weight:bold">${dogPoints} pts</div>
            </div>
            <div class="dog-breed">${a.breed} ${"M" === a.gender ? '♂' : '♀'}</div>
            <div style="font-size:12px;color:#666">Nível: ${a.level} • Renda: ${i.toFixed(2)}/s</div>
            ${a.traits && a.traits.length > 0 ? 
                `<div style="font-size:11px;color:#28a745;margin:5px 0">
                    🏷️ ${a.traits.map(tr => tr.name).join(", ")}
                    ${a.traits.length > 1 ? `<span style="font-size:9px;color:#666">(${a.traits.length} traços)</span>` : ''}
                </div>` 
            : ""}
            <div style="margin:8px 0">
                <div style="font-size:11px;color:#666">Fome: ${Math.round(a.hunger)}%</div>
                <div class="progress-container">
                    <div class="progress-bar" style="width:${a.hunger}%;background:${a.hunger > 50 ? "#4caf50" : a.hunger > 25 ? "#ff9800" : "#f44336"}"></div>
                </div>
            </div>
            <div style="display:flex;gap:5px;margin-top:10px">
                <button class="btn" style="flex:1;background:#${"M" === a.gender ? "2196F3" : "E91E63"};color:#fff" onclick="selecionarParaBreeding(${o})">${l ? "✓ Selecionado" : "Selecionar"}</button>
                <button class="btn" style="background:#6c757d;color:#fff;font-size:10px;padding:5px" onclick="mostrarDetalhesCao(${o})">ℹ️</button>
                <button class="btn" style="background:#17a2b8;color:#fff;font-size:10px;padding:5px" onclick="darNomeCao(${o}, false)" title="Mudar nome">✏️</button>
                ${podeSacrificar ? `<button class="btn" style="background:#dc3545;color:#fff;font-size:10px;padding:5px" onclick="sacrificarCao(${o})" title="Sacrificar cão (Custo: ${getCurrentSacrificeCost()} moedas)">⚰️</button>` : ''}
            </div>
        </div>`;
    });
    
    if (canSacrifice()) {
        t += `
        <div class="dog-card" style="background:#f8f9fa;border:2px dashed #dc3545;">
            <div style="text-align:center;padding:10px;">
                <h4 style="margin:0 0 10px 0;color:#dc3545">⚰️ Sistema de Sacrifício</h4>
                <p style="font-size:12px;color:#666;margin:0 0 10px 0;">
                    Clínica nível 5 desbloqueada! Você pode sacrificar cães por recompensas.
                </p>
                <div style="background:#fff;padding:8px;border-radius:5px;margin-bottom:10px;">
                    <div style="font-size:11px;color:#666">Cães sacrificados: <strong>${sacrificeCount}</strong></div>
                    <div style="font-size:11px;color:#666">Próximo custo: <strong>${getCurrentSacrificeCost()}</strong> moedas</div>
                </div>
                <button class="btn" style="background:#dc3545;color:#fff;font-size:12px;width:100%" onclick="mostrarInfoSacrificio()">
                    ℹ️ Saiba mais
                </button>
            </div>
        </div>`;
    }
    
    t += "</div>";
    e.innerHTML = t;
    updateDogCardsRarity();
}

// CORREÇÃO: Função darNomeCao atualizada
function darNomeCao(dogIndex, isNewDog = false) {
    const dog = dogs[dogIndex];
    if (!dog) return;
    
    const promptMessage = isNewDog 
        ? `🎉 Novo ${dog.gender === "M" ? "cão macho" : "cadela fêmea"} (${dog.breed})!\n\nDigite um nome para seu novo amigo:`
        : `✏️ Editar nome do cão ${dogIndex + 1} (${dog.breed})\n\nDigite o novo nome:`;
    
    const nomeAtual = dog.name || "";
    const novoNome = prompt(promptMessage, nomeAtual);
    
    // CORREÇÃO: Verificação de cancelamento
    if (novoNome === null) return; // Usuário cancelou
    
    if (novoNome.trim() !== "") {
        const nomeLimpo = novoNome.trim().substring(0, 20);
        const nomeExistente = dogs.some((d, idx) => idx !== dogIndex && d.name === nomeLimpo);
        
        if (nomeExistente) {
            if (!confirm(`Já existe um cão chamado "${nomeLimpo}".\nDeseja usar mesmo assim?`)) {
                darNomeCao(dogIndex, isNewDog);
                return;
            }
        }
        
        dog.name = nomeLimpo;
        dog.customName = true;
        renderDogsList();
        atualizarSelecaoBreeding();
        
        if (isNewDog) {
            alert(`✨ Perfeito! Seu novo cão se chama ${nomeLimpo}!`);
        } else {
            alert(`✅ Nome alterado para ${nomeLimpo}!`);
        }
        
        salvarJogo();
    } else if (novoNome.trim() === "") {
        alert("❌ O nome não pode estar vazio!");
        darNomeCao(dogIndex, isNewDog);
    }
}

function mostrarDetalhesCao(e) {
    const t = dogs[e];
    if (!t) return;
    
    let a = t.baseIncome || .1;
    
    // Aplica bônus de traço Rico
    if (t.traits) {
        t.traits.forEach(trait => {
            if (trait.name === "Rico") {
                a += trait.coinBonus || 0.1;
            }
        });
    }
    
    a *= 1 + rebirthBonus.incomeMultiplier / 100;
    
    const tarefaAtiva = activeTasks.find(task => task.dogIndex === e && !task.completed);
    const dogPoints = calculateDogPoints(t);
    const breedInfo = breedRarityPoints[t.breed] || { points: 10, rarity: "common" };
    const nomeCao = t.name || `Cão ${e + 1}`;
    
    let info = `🐕 ${nomeCao}
🎖️ Raça: ${t.breed} (${breedInfo.rarity.charAt(0).toUpperCase() + breedInfo.rarity.slice(1)})
⚤ Gênero: ${"M" === t.gender ? "Macho ♂" : "Fêmea ♀"}
📊 Nível: ${t.level}
⭐ EXP: ${Math.floor(t.exp)}/100
💰 Renda: ${a.toFixed(2)}/s
🏆 Pontos: ${dogPoints} ${dogPoints > (breedRarityPoints[t.breed]?.points || 10) ? "(+ bônus)" : ""}
🍖 Fome: ${Math.round(t.hunger)}%`;
    
    if (t.traits && t.traits.length > 0) {
        info += `\n🏷️ Traços: ${t.traits.map(tr => tr.name).join(", ")}`;
    }
    
    if (tarefaAtiva) {
        const taskInfo = tasks[tarefaAtiva.taskType][tarefaAtiva.taskIndex];
        const elapsed = Date.now() - tarefaAtiva.startTime;
        const remaining = Math.max(0, tarefaAtiva.duration - elapsed);
        info += `\n⏳ Trabalhando: ${taskInfo.name} (${formatarTempo(remaining / 1000)} restante)`;
    }
    
    info += `\n${t.parents ? `👨‍👩‍👧 Filho de: ${t.parents[0]} + ${t.parents[1]}` : ""}`;
    info += `\n\n📝 Opções:\n1. Mudar nome\n2. Fechar`;
    
    const escolha = prompt(info, "2");
    if (escolha === "1") darNomeCao(e, false);
}

function getRebirthRequirement() {
    return 10000 * Math.pow(2, prestigeLevel);
}

function getDogCapacity() {
    let e = 2;
    if (casinhaLevel >= 1) e++;
    if (casinhaLevel >= 5) e++;
    e += rebirthBonus.extraCapacity;
    return e;
}

function realizarRebirth() {
    const e = getRebirthRequirement();
    if (moedas < e) {
        alert(`Você precisa de ${formatarNumero(e)} moedas para fazer rebirth!`);
        return;
    }
    
    if (!confirm("Deseja fazer rebirth? Você perderá todos os cães, itens e moedas, mas ganhará +1 prestígio com bônus permanentes e pontos!")) return;
    
    prestigeLevel++;
    rebirthBonus.incomeMultiplier += 5;
    rebirthBonus.resourceMultiplier += 10;
    rebirthBonus.extraCapacity += 1;
    moedas = 0;
    food = 0;
    agua = 0;
    casinhaLevel = 0;
    bebedouroLevel = 0;
    comedouroLevel = 0;
    brinquedoLevel = 0;
    atividadeLevel = 0;
    clinicaLevel = 0;
    dogs = [];
    selectedDogs = [];
    
    // RESETAR SISTEMA DE COMPRA DE CÃES TAMBÉM
    comprasDeCaes = 0;
    
    // RESETAR SISTEMAS DE BÔNUS
    doubleExpActive = false;
    doubleExpEndTime = 0;
    doubleExpCooldownEndTime = 0;
    hidratacaoActive = false;
    hidratacaoEndTime = 0;
    hidratacaoCooldownEndTime = 0;
    
    sacrificeCount = 0;
    sacrificeCost = 1000;
    temporaryIncomeBonus = 0;
    temporaryIncomeBonusEndTime = 0;
    
    activeTasks = [];
    salvarTarefasAtivas();
    
    updatePointsSystem();
    alert(`🎉 REBIRTH CONCLUÍDO! Prestígio ${prestigeLevel}\n\nSistema de compra de cães resetado. Preços voltaram ao normal.`);
    atualizarUI();
    salvarJogo();
}

function atualizarRebirthUI() {
    const e = getRebirthRequirement();
    const t = Math.min(moedas / e * 100, 100);
    
    document.getElementById("rebirthRequirement").textContent = formatarNumero(e);
    document.getElementById("rebirthProgressBar").style.width = `${t}%`;
    document.getElementById("rebirthProgressText").textContent = `Progresso: ${t.toFixed(1)}%`;
    document.getElementById("rebirthBtn").disabled = moedas < e;
    document.getElementById("currentPrestige").textContent = prestigeLevel;
    document.getElementById("currentIncomeBonus").textContent = rebirthBonus.incomeMultiplier;
    document.getElementById("currentCapacityBonus").textContent = rebirthBonus.extraCapacity;
    document.getElementById("currentResourceBonus").textContent = rebirthBonus.resourceMultiplier;
    document.getElementById("rebirthBtnHeader").disabled = moedas < e;
    document.getElementById("rebirthBtnHeader").textContent = moedas < e ? "🔄 Rebirth" : "🎉 REBIRTH DISPONÍVEL!";
}

function formatarNumero(e) {
    if (e >= 1000000) return (e / 1000000).toFixed(2) + "M";
    if (e >= 1000) return (e / 1000).toFixed(2) + "K";
    return e.toFixed(2);
}

function updateUpgradeButtonLabel(e, t) {
    const a = document.getElementById(`upgrade${e.charAt(0).toUpperCase() + e.slice(1)}Btn`);
    if (!a) return;
    
    if (0 === t) {
        a.innerText = "Construa antes";
        a.disabled = true;
    } else if (t >= 5) {
        a.innerText = "Nível MAX";
        a.disabled = true;
    } else {
        a.innerText = `Upgrade (${upgradeCosts[t + 1]})`;
        a.disabled = false;
    }
}

function selecionarParaBreeding(e) {
    const t = dogs[e];
    if (!t || !t.alive) return;
    
    if (selectedDogs.includes(e)) {
        selectedDogs = selectedDogs.filter(a => a !== e);
    } else {
        if (selectedDogs.length >= 2) {
            alert("Você já selecionou 2 cães para cruzamento!");
            return;
        }
        if (1 === selectedDogs.length && dogs[selectedDogs[0]].gender === t.gender) {
            alert("Os cães precisam ser de gêneros diferentes!");
            return;
        }
        selectedDogs.push(e);
    }
    
    atualizarSelecaoBreeding();
    renderDogsList();
}

function atualizarSelecaoBreeding() {
    if (selectedDogs.length >= 1) {
        const e = dogs[selectedDogs[0]];
        const nomeCao1 = e.name || `Cão ${selectedDogs[0] + 1}`;
        document.getElementById("selectedDog1").textContent = `${nomeCao1}`;
        document.getElementById("selectedDog1Info").textContent = `${e.breed} • Nível ${e.level} • ${"M" === e.gender ? "♂" : "♀"}`;
    } else {
        document.getElementById("selectedDog1").textContent = "---";
        document.getElementById("selectedDog1Info").textContent = "";
    }
    
    if (selectedDogs.length >= 2) {
        const e = dogs[selectedDogs[1]];
        const nomeCao2 = e.name || `Cão ${selectedDogs[1] + 1}`;
        document.getElementById("selectedDog2").textContent = `${nomeCao2}`;
        document.getElementById("selectedDog2Info").textContent = `${e.breed} • Nível ${e.level} • ${"M" === e.gender ? "♂" : "♀"}`;
        
        let t = 60;
        const a = dogs[selectedDogs[0]];
        t += Math.min(a.level + e.level, 40);
        
        // Aplica bônus de traço Fértil
        [a, e].forEach(parent => {
            if (parent.traits) {
                parent.traits.forEach(trait => {
                    if (trait.name === "Fértil") {
                        t += 2; // +2% por cada traço Fértil
                    }
                });
            }
        });
        
        t = Math.min(t, 95);
        
        const o = breedingCost + (a.level + e.level) * 50;
        document.getElementById("breedingChance").textContent = `${t}%`;
        document.getElementById("breedingCost").textContent = o;
        document.getElementById("startBreedingBtn").disabled = false;
        document.getElementById("startBreedingBtn").innerHTML = `🐾 CRUZAR (${o} moedas)`;
    } else {
        document.getElementById("selectedDog2").textContent = "---";
        document.getElementById("selectedDog2Info").textContent = "";
        document.getElementById("breedingChance").textContent = "0%";
        document.getElementById("breedingCost").textContent = "0";
        document.getElementById("startBreedingBtn").disabled = true;
        document.getElementById("startBreedingBtn").innerHTML = "SELECIONE 2 CÃES";
    }
}

// ============================================
// FUNÇÕES DO NOVO SISTEMA DE COMPRA DE CÃES
// ============================================

function getCurrentDogPrice() {
    return Math.floor(precoBaseCao * Math.pow(multiplicadorPreco, comprasDeCaes));
}

function getBreedChances() {
    const chances = {};
    let totalWeight = 0;
    
    // Calcular pesos ajustados baseados nos pontos
    for (const [breed, data] of Object.entries(breedRarityWeights)) {
        if (totalPoints >= data.minPoints) {
            // Aumentar peso baseado nos pontos (cada 100 pontos = +1% de peso)
            const bonusWeight = Math.floor(totalPoints / 100) * 1;
            const adjustedWeight = data.baseWeight + bonusWeight;
            chances[breed] = adjustedWeight;
            totalWeight += adjustedWeight;
        } else {
            chances[breed] = 0;
        }
    }
    
    // Se nenhuma raça está disponível, forçar Vira-lata
    if (totalWeight === 0) {
        chances["Vira-lata"] = 100;
        totalWeight = 100;
    }
    
    // Converter para porcentagens
    const percentages = {};
    for (const [breed, weight] of Object.entries(chances)) {
        if (weight > 0) {
            percentages[breed] = (weight / totalWeight) * 100;
        }
    }
    
    return percentages;
}

function chooseBreedBasedOnPoints() {
    const chances = getBreedChances();
    
    // Criar array de raças com pesos acumulados
    const weightedBreeds = [];
    for (const [breed, percentage] of Object.entries(chances)) {
        if (percentage > 0) {
            weightedBreeds.push({
                breed: breed,
                weight: percentage
            });
        }
    }
    
    // Escolher aleatoriamente baseado nos pesos
    const random = Math.random() * 100;
    let accumulated = 0;
    
    for (const weightedBreed of weightedBreeds) {
        accumulated += weightedBreed.weight;
        if (random <= accumulated) {
            // Encontrar os dados completos da raça
            return breeds.find(b => b.name === weightedBreed.breed) || breeds[0];
        }
    }
    
    // Fallback
    return breeds[0];
}

// CORREÇÃO: Mover updateChancesDisplay para antes do window.onload
function updateChancesDisplay() {
    // Adicionar ou atualizar display de chances na UI
    let chancesDisplay = document.getElementById("chancesDisplay");
    if (!chancesDisplay) {
        chancesDisplay = document.createElement("div");
        chancesDisplay.id = "chancesDisplay";
        chancesDisplay.style.position = "fixed";
        chancesDisplay.style.bottom = "10px";
        chancesDisplay.style.right = "10px";
        chancesDisplay.style.background = "rgba(255, 255, 255, 0.9)";
        chancesDisplay.style.padding = "10px";
        chancesDisplay.style.borderRadius = "8px";
        chancesDisplay.style.boxShadow = "0 2px 10px rgba(0,0,0,0.2)";
        chancesDisplay.style.fontSize = "11px";
        chancesDisplay.style.zIndex = "999";
        chancesDisplay.style.maxWidth = "250px";
        document.body.appendChild(chancesDisplay);
    }
    
    const chances = getBreedChances();
    let html = `<div style="font-weight:bold;margin-bottom:5px;color:#333">🎯 Chances por Pontos: ${totalPoints}</div>`;
    
    for (const [breed, percentage] of Object.entries(chances)) {
        if (percentage > 0) {
            const breedInfo = breedRarityPoints[breed] || { rarity: "common" };
            const barWidth = Math.min(100, percentage * 2); // Aumentar visualmente
            
            html += `
            <div style="margin-bottom:3px;">
                <div style="display:flex;justify-content:space-between;font-size:10px;">
                    <span>${breed}</span>
                    <span style="font-weight:bold">${percentage.toFixed(1)}%</span>
                </div>
                <div class="progress-container" style="height:4px;margin:2px 0;">
                    <div class="progress-bar" style="width:${barWidth}%;background:${getRarityColor(breedInfo.rarity)}"></div>
                </div>
            </div>
            `;
        }
    }
    
    html += `<div style="font-size:9px;color:#666;margin-top:5px;">💰 Próximo cão: ${getCurrentDogPrice()} moedas</div>`;
    chancesDisplay.innerHTML = html;
}

function getRarityColor(rarity) {
    const colors = {
        "common": "#6c757d",
        "uncommon": "#28a745",
        "rare": "#007bff",
        "epic": "#6f42c1",
        "legendary": "#fd7e14"
    };
    return colors[rarity] || "#6c757d";
}

// ============================================
// EVENT LISTENERS
// ============================================

document.getElementById("startBreedingBtn").addEventListener("click", () => {
    if (2 !== selectedDogs.length) return;
    
    const e = dogs[selectedDogs[0]];
    const t = dogs[selectedDogs[1]];
    const a = breedingCost + (e.level + t.level) * 50;
    
    if (moedas < a) {
        alert("Moedas insuficientes!");
        return;
    }
    
    let o = 60;
    o += Math.min(e.level + t.level, 40);
    
    // Aplica bônus de traço Fértil
    [e, t].forEach(parent => {
        if (parent.traits) {
            parent.traits.forEach(trait => {
                if (trait.name === "Fértil") {
                    o += 2; // +2% por cada traço Fértil
                }
            });
        }
    });
    
    o = Math.min(o, 95);
    
    const l = 100 * Math.random() < o;
    
    moedas -= a;
    
    if (l) {
        const a = getDogCapacity();
        if (dogs.filter(e => e.alive).length >= a) {
            alert("Capacidade máxima atingida!");
            return;
        }
        
        const nomesFilhotes = ["Junior", "Filhote", "Herdeiro", "Novo", "Pequeno"];
        const nomeFilhote = nomesFilhotes[Math.floor(Math.random() * nomesFilhotes.length)];
        
        const l = {
            hunger: 100,
            alive: true,
            exp: 0,
            level: 1,
            gender: Math.random() < .5 ? "M" : "F",
            breed: e.breed,
            breedColor: e.breedColor,
            baseIncome: 1.1 * e.baseIncome,
            traits: inheritTraits(e, t), // Herda traços dos pais
            parents: [e.breed, t.breed],
            name: nomeFilhote,
            customName: false
        };
        
        dogs.push(l);
        document.getElementById("breedingResult").innerHTML = `
            <div style="background:#d4edda;color:#155724;padding:15px;border-radius:8px;text-align:center">
                🎉 Filhote nascido! Um lindo ${l.breed} ${"M" === l.gender ? "macho" : "fêmea"}!
                ${l.traits && l.traits.length > 0 ? `<br>🏷️ Traços herdados: ${l.traits.map(t => t.name).join(", ")}` : ''}
            </div>
        `;
        
        setTimeout(() => {
            darNomeCao(dogs.length - 1, true);
        }, 1000);
        
        updatePointsSystem();
    } else {
        document.getElementById("breedingResult").innerHTML = `
            <div style="background:#f8d7da;color:#721c24;padding:15px;border-radius:8px;text-align:center">
                ❌ Cruzamento falhou! Tente novamente.
            </div>
        `;
    }
    
    selectedDogs = [];
    atualizarUI();
});

document.getElementById("clearSelectionBtn").addEventListener("click", () => {
    selectedDogs = [];
    atualizarSelecaoBreeding();
    renderDogsList();
});

// FUNÇÃO ÚNICA DE COMPRAR CÃO (ATUALIZADA)
document.getElementById("comprarCaoBtn").addEventListener("click", function comprarCaoHandler() {
    if (0 == casinhaLevel) {
        alert("Construa a casinha primeiro!");
        return;
    }
    
    const capacidade = getDogCapacity();
    if (dogs.filter(dog => dog.alive).length >= capacidade) {
        alert("Capacidade máxima!");
        return;
    }
    
    const precoAtual = getCurrentDogPrice();
    if (moedas < precoAtual) {
        alert(`Moedas insuficientes! Preço atual: ${precoAtual}`);
        return;
    }
    
    moedas -= precoAtual;
    comprasDeCaes++; // Incrementar contador de compras
    
    const genero = genders[Math.floor(Math.random() * genders.length)];
    const raca = chooseBreedBasedOnPoints(); // Usar nova função baseada em pontos
    
    const nomesMasculinos = ["Rex", "Thor", "Max", "Bobby", "Tobby", "Zeus", "Apollo", "Rocky", "Duke", "Charlie"];
    const nomesFemininos = ["Luna", "Bella", "Daisy", "Molly", "Lola", "Sadie", "Maggie", "Sophie", "Chloe", "Bailey"];
    const nomePadrao = genero === "M" 
        ? nomesMasculinos[Math.floor(Math.random() * nomesMasculinos.length)]
        : nomesFemininos[Math.floor(Math.random() * nomesFemininos.length)];
    
    const novoCao = {
        hunger: 100,
        alive: true,
        exp: 0,
        level: 1,
        gender: genero,
        breed: raca.name,
        breedColor: raca.color,
        baseIncome: raca.baseIncome,
        traits: [], // Começa sem traços
        name: nomePadrao,
        customName: false,
        purchased: true, // Marcar como comprado (não nascido de breeding)
        purchaseNumber: comprasDeCaes // Número da compra
    };
    
    // Adiciona traço aleatório (30% Fértil, 20% Brincalhão, 20% Trabalhador, 10% Rico, 10% Poseidon, 10% sem traço)
    const randomTrait = getRandomTrait();
    if (randomTrait) {
        novoCao.traits.push(randomTrait);
    }
    
    dogs.push(novoCao);
    
    // Mostrar informações sobre a raridade
    const breedInfo = breedRarityPoints[raca.name] || { points: 10, rarity: "common" };
    const rarityName = breedInfo.rarity.charAt(0).toUpperCase() + breedInfo.rarity.slice(1);
    
    setTimeout(() => {
        darNomeCao(dogs.length - 1, true);
    }, 500);
    
    // Atualizar UI e mostrar mensagem informativa
    updatePointsSystem();
    atualizarUI();
    
    // Atualizar botão de compra com novo preço
    document.getElementById("comprarCaoBtn").textContent = `🐕 Comprar Cão (${getCurrentDogPrice()})`;
    
    // Mostrar mensagem sobre a raridade e traço
    const rarityMessages = {
        "common": "🐕 Um Vira-lata comum chegou ao canil!",
        "uncommon": "🐩 Um Poodle incomum! Boa aquisição!",
        "rare": "🐺 Um Pastor Alemão raro! Excelente!",
        "epic": "🌟 Um Golden Retriever épico! Incrível!",
        "legendary": "💫✨ UM HUSKY SIBERIANO LENDÁRIO! JACKPOT! ✨💫"
    };
    
    const traitMessage = randomTrait ? `\n🏷️ Traço adquirido: ${randomTrait.name}` : "\n🏷️ Sem traço especial";
    
    alert(`${rarityMessages[breedInfo.rarity] || "Novo cão adquirido!"}${traitMessage}\n\n` +
          `🏆 Raridade: ${rarityName}\n` +
          `💰 Preço pago: ${precoAtual} moedas\n` +
          `📈 Próximo cão custará: ${getCurrentDogPrice()} moedas\n` +
          `🎯 Pontos atuais: ${totalPoints} (afetam as chances)`);
    
    salvarJogo();
});

document.getElementById("buyFoodBtn").addEventListener("click", () => {
    if (moedas < 1) {
        alert("Moedas insuficientes");
        return;
    }
    moedas -= 1;
    food += 1;
    atualizarUI();
});

document.getElementById("buildCasinhaBtn").addEventListener("click", () => {
    if (casinhaLevel > 0) {
        alert("Já construída");
        return;
    }
    if (moedas < 200) {
        alert("Moedas insuficientes");
        return;
    }
    moedas -= 200;
    casinhaLevel = 1;
    atualizarUI();
    alert("Casinha construída!");
});

document.getElementById("buildBebedouroBtn").addEventListener("click", () => {
    if (bebedouroLevel > 0) {
        alert("Já construído");
        return;
    }
    if (moedas < 500) {
        alert("Moedas insuficientes");
        return;
    }
    moedas -= 500;
    bebedouroLevel = 1;
    atualizarUI();
    alert("Bebedouro construído!");
});

document.getElementById("buildComedouroBtn").addEventListener("click", () => {
    if (comedouroLevel > 0) {
        alert("Já construído");
        return;
    }
    if (moedas < 500) {
        alert("Moedas insuficientes");
        return;
    }
    moedas -= 500;
    comedouroLevel = 1;
    atualizarUI();
    alert("Comedouro construído!");
});

// NOVOS BOTÕES PARA BRINQUEDO E ATIVIDADE
document.getElementById("buildBrinquedoBtn").addEventListener("click", () => {
    if (brinquedoLevel > 0) {
        alert("Já construído");
        return;
    }
    if (moedas < 500) {
        alert("Moedas insuficientes");
        return;
    }
    moedas -= 500;
    brinquedoLevel = 1;
    atualizarUI();
    alert("Brinquedo construído! Agora você pode melhorá-lo usando comida e água.");
});

document.getElementById("upgradeBrinquedoBtn").addEventListener("click", upgradeBrinquedo);

document.getElementById("buildAtividadeBtn").addEventListener("click", () => {
    if (atividadeLevel > 0) {
        alert("Já construída");
        return;
    }
    if (moedas < 500) {
        alert("Moedas insuficientes");
        return;
    }
    moedas -= 500;
    atividadeLevel = 1;
    atualizarUI();
    alert("Área de Atividade construída! Agora você pode melhorá-la usando água.");
});

document.getElementById("upgradeAtividadeBtn").addEventListener("click", upgradeAtividade);

document.getElementById("buildClinicaBtn").addEventListener("click", () => {
    if (clinicaLevel > 0) {
        alert("Já construída");
        return;
    }
    if (moedas < 500) {
        alert("Moedas insuficientes");
        return;
    }
    moedas -= 500;
    clinicaLevel = 1;
    atualizarUI();
    alert("Clínica construída!");
});

function tryUpgrade(e) {
    let t = () => eval(`${e}Level`);
    let a = t();
    
    if (0 === a) {
        alert("Construa antes");
        return;
    }
    if (a >= 5) {
        alert("Nível máximo");
        return;
    }
    
    const o = upgradeCosts[a + 1];
    if (moedas < o) {
        alert("Moedas insuficientes");
        return;
    }
    
    moedas -= o;
    eval(`${e}Level++`);
    atualizarUI();
    alert(`${e.charAt(0).toUpperCase() + e.slice(1)} atualizado para nível ${t()}`);
}

document.getElementById("upgradeCasinhaBtn").addEventListener("click", () => tryUpgrade("casinha"));
document.getElementById("upgradeBebedouroBtn").addEventListener("click", () => tryUpgrade("bebedouro"));
document.getElementById("upgradeComedouroBtn").addEventListener("click", () => tryUpgrade("comedouro"));
document.getElementById("upgradeClinicaBtn").addEventListener("click", () => tryUpgrade("clinica"));

function spawnLixo() {
    document.getElementById("lixoModal").style.display = "block";
    document.getElementById("eventOverlay").style.display = "block";
}

function spawnPulga() {
    document.getElementById("pulgaModal").style.display = "block";
    document.getElementById("eventOverlay").style.display = "block";
}

function coletarLixo() {
    moedas += 20;
    dogs.forEach((e, t) => {
        e.alive && ganharExp(t, 5);
    });
    document.getElementById("lixoModal").style.display = "none";
    document.getElementById("eventOverlay").style.display = "none";
    atualizarUI();
}

function coletarPulga() {
    moedas += 10;
    dogs.forEach((e, t) => {
        e.alive && ganharExp(t, 10);
    });
    document.getElementById("pulgaModal").style.display = "none";
    document.getElementById("eventOverlay").style.display = "none";
    atualizarUI();
}

setInterval(spawnLixo, 120000);
setInterval(spawnPulga, 300000);

document.getElementById("eventOverlay").addEventListener("click", function() {
    document.querySelectorAll(".event-modal").forEach(e => e.style.display = "none");
    this.style.display = "none";
});

function salvarJogo() {
    const e = {
        moedas, food, agua, dogs, casinhaLevel, bebedouroLevel,
        comedouroLevel, brinquedoLevel, atividadeLevel, clinicaLevel,
        prestigeLevel, rebirthBonus, timestamp: Date.now(),
        totalPoints, pointsFromRebirths, pointsFromDogs,
        sacrificeCount, sacrificeCost, sacrificeCostMultiplier,
        temporaryIncomeBonus, temporaryIncomeBonusEndTime,
        comprasDeCaes, precoBaseCao, multiplicadorPreco,
        doubleExpActive, doubleExpEndTime, doubleExpCooldownEndTime,
        hidratacaoActive, hidratacaoEndTime, hidratacaoCooldownEndTime
    };
    localStorage.setItem("canilClickerSave", JSON.stringify(e));
}

function carregarJogo() {
    try {
        const e = localStorage.getItem("canilClickerSave");
        if (e) {
            const saveData = JSON.parse(e);
            
            prestigeLevel = saveData.prestigeLevel || 0;
            rebirthBonus = saveData.rebirthBonus || {incomeMultiplier: 0, resourceMultiplier: 0, extraCapacity: 0};
            moedas = saveData.moedas || 0;
            food = saveData.food || 0;
            agua = saveData.agua || 0;
            dogs = saveData.dogs || [];
            casinhaLevel = saveData.casinhaLevel || 0;
            bebedouroLevel = saveData.bebedouroLevel || 0;
            comedouroLevel = saveData.comedouroLevel || 0;
            brinquedoLevel = saveData.brinquedoLevel || 0;
            atividadeLevel = saveData.atividadeLevel || 0;
            clinicaLevel = saveData.clinicaLevel || 0;
            
            totalPoints = saveData.totalPoints || 0;
            pointsFromRebirths = saveData.pointsFromRebirths || 0;
            pointsFromDogs = saveData.pointsFromDogs || 0;
            
            sacrificeCount = saveData.sacrificeCount || 0;
            sacrificeCost = saveData.sacrificeCost || 1000;
            sacrificeCostMultiplier = saveData.sacrificeCostMultiplier || 1.5;
            temporaryIncomeBonus = saveData.temporaryIncomeBonus || 0;
            temporaryIncomeBonusEndTime = saveData.temporaryIncomeBonusEndTime || 0;
            
            // CARREGAR NOVAS VARIÁVEIS
            comprasDeCaes = saveData.comprasDeCaes || 0;
            precoBaseCao = saveData.precoBaseCao || 200;
            multiplicadorPreco = saveData.multiplicadorPreco || 1.1;
            
            // CARREGAR VARIÁVEIS DOS NOVOS SISTEMAS
            doubleExpActive = saveData.doubleExpActive || false;
            doubleExpEndTime = saveData.doubleExpEndTime || 0;
            doubleExpCooldownEndTime = saveData.doubleExpCooldownEndTime || 0;
            hidratacaoActive = saveData.hidratacaoActive || false;
            hidratacaoEndTime = saveData.hidratacaoEndTime || 0;
            hidratacaoCooldownEndTime = saveData.hidratacaoCooldownEndTime || 0;
            
            dogs.forEach((dog, index) => {
                if (!dog.name) {
                    const nomesMasculinos = ["Rex", "Thor", "Max", "Bobby", "Tobby", "Zeus", "Apollo", "Rocky", "Duke", "Charlie"];
                    const nomesFemininos = ["Luna", "Bella", "Daisy", "Molly", "Lola", "Sadie", "Maggie", "Sophie", "Chloe", "Bailey"];
                    dog.name = dog.gender === "M" 
                        ? nomesMasculinos[Math.floor(Math.random() * nomesMasculinos.length)]
                        : nomesFemininos[Math.floor(Math.random() * nomesFemininos.length)];
                    dog.customName = false;
                }
            });
        }
    } catch (error) {
        console.error("Erro ao carregar jogo:", error);
        // Inicializar com valores padrão
        prestigeLevel = 0;
        rebirthBonus = {incomeMultiplier: 0, resourceMultiplier: 0, extraCapacity: 0};
        moedas = 0;
        food = 0;
        agua = 0;
        dogs = [];
        casinhaLevel = 0;
        bebedouroLevel = 0;
        comedouroLevel = 0;
        brinquedoLevel = 0;
        atividadeLevel = 0;
        clinicaLevel = 0;
    }
    
    carregarTarefasAtivas();
}

setInterval(salvarJogo, 10000);

function criarEfeitoMoeda(e) {
    const t = e.clientX || 100;
    const a = e.clientY || 100;
    const o = document.createElement("div");
    o.innerText = "+1";
    o.style.position = "fixed";
    o.style.left = t + "px";
    o.style.top = a + "px";
    o.style.color = "#FFD700";
    o.style.fontWeight = "bold";
    o.style.fontSize = "20px";
    o.style.zIndex = "10000";
    o.style.pointerEvents = "none";
    document.body.appendChild(o);
    o.animate([
        {opacity: 1, transform: "translateY(0) scale(1)"},
        {opacity: 0, transform: "translateY(-50px) scale(1.5)"}
    ], 1000).onfinish = () => o.remove();
}

setInterval(() => {
    const baseResourceMultiplier = 1 + rebirthBonus.resourceMultiplier / 100;
    
    // Geração base de recursos
    let waterGeneration = 0.1 * bebedouroLevel * baseResourceMultiplier;
    let foodGeneration = 0.1 * comedouroLevel * baseResourceMultiplier;
    
    // Aplica bônus de Hidratação
    if (hidratacaoActive) {
        waterGeneration *= 2;
    }
    
    // Aplica bônus dos traços de todos os cães vivos
    dogs.forEach(dog => {
        if (!dog.alive) return;
        
        // Consumo de comida
        let t = foodConsumptionPerDog;
        if (food >= t) {
            food -= t;
            dog.hunger = Math.min(100, dog.hunger + 1);
        } else {
            dog.hunger = Math.max(0, dog.hunger - 0.5);
        }
        
        // Aplica bônus de traços para geração de recursos
        if (dog.traits) {
            dog.traits.forEach(trait => {
                if (trait.name === "Poseidon") {
                    waterGeneration += trait.waterBonus || 0.1;
                }
                if (trait.name === "Brincalhão") {
                    foodGeneration += trait.foodBonus || 0.05;
                }
            });
        }
        
        if (dog.hunger <= 0) {
            dog.alive = false;
            const nomeCao = dog.name || `Cão ${dogs.indexOf(dog) + 1}`;
            alert(`Seu cão ${nomeCao} (${dog.breed}) morreu de fome!`);
        }
        
        // Sistema de nível antigo (sem ganhar traços ao subir de nível)
        if (dog.exp >= 100) {
            dog.exp -= 100;
            dog.level++;
            updatePointsSystem();
        }
    });
    
    agua += waterGeneration;
    food += foodGeneration;
    
    atualizarRenda();
    moedas += rendaTotal;
    verificarTarefasCompletas();
    updateBonusTimers();
    atualizarUI();
    
    if (temporaryIncomeBonus > 0 && Date.now() > temporaryIncomeBonusEndTime) {
        temporaryIncomeBonus = 0;
        const bonusIndicator = document.getElementById("temporaryBonusIndicator");
        if (bonusIndicator) bonusIndicator.remove();
    }
}, 1000);

function ganharExp(e, t) {
    dogs[e] && (dogs[e].exp += t);
}

document.getElementById("rebirthBtn").addEventListener("click", realizarRebirth);

function mostrarInfoSacrificio() {
    const info = `⚰️ SISTEMA DE SACRIFÍCIO\n\n` +
                 `Com a Clínica no nível 5, você pode sacrificar cães por recompensas.\n\n` +
                 `🎯 COMO FUNCIONA:\n` +
                 `• Selecione um cão vivo\n` +
                 `• Pague o custo atual (${getCurrentSacrificeCost()} moedas)\n` +
                 `• Receba recompensas baseadas no cão\n\n` +
                 `🎁 RECOMPENSAS:\n` +
                 `• 50% do custo em moedas\n` +
                 `• 75% dos pontos do cão\n` +
                 `• +5% de renda por 60 segundos\n\n` +
                 `⚠️ REGRAS:\n` +
                 `• Custo aumenta 50% a cada sacrifício\n` +
                 `• Necessário ter pelo menos 1 cão vivo\n` +
                 `• Cão sacrificado é removido permanentemente\n\n` +
                 `💰 Custo atual: ${getCurrentSacrificeCost()} moedas\n` +
                 `📈 Cães sacrificados: ${sacrificeCount}`;
    
    alert(info);
}

// ============================================
// INICIALIZAÇÃO
// ============================================
window.onload = function() {
    carregarJogo();
    carregarTarefasAtivas();
    atualizarUI();
    updatePointsSystem();
    
    // Iniciar atualização periódica das chances
    setTimeout(function() {
        if (typeof updateChancesDisplay === 'function') {
            setInterval(updateChancesDisplay, 5000);
            updateChancesDisplay(); // Chamar uma vez imediatamente
        }
    }, 1000);
    
    setInterval(verificarTarefasCompletas, 1000);
};

atualizarUI();
setInterval(verificarTarefasCompletas, 1000);
</script>
</body>
</html>
