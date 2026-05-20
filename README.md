# ProjetoMultidiscipliar-Front-End
Projeto Multidisciplinar Ênfase: Desenvolvimento Front-End (SGHSS)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>SGHSS VidaPlus - Simulador</title>
  <style>
    :root{
      --bg:#f4f6fb;
      --card:#ffffff;
      --text:#1f2937;
      --muted:#6b7280;
      --primary:#2563eb;
      --primary-2:#1d4ed8;
      --success:#16a34a;
      --danger:#dc2626;
      --warning:#f59e0b;
      --info:#0ea5e9;
      --gray:#9ca3af;
      --shadow:0 8px 24px rgba(17,24,39,.08);
      --radius:12px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:Inter,Segoe UI,Roboto,Arial,sans-serif;
      color:var(--text);
      background:var(--bg);
    }
    .hidden{display:none !important}
    .app{display:flex;min-height:100vh}
    .sidebar{
      width:260px;
      background:#0f172a;
      color:#e2e8f0;
      padding:20px 14px;
      display:flex;
      flex-direction:column;
      gap:14px;
      position:sticky;
      top:0;
      height:100vh;
    }
    .brand{font-size:20px;font-weight:800;letter-spacing:.2px}
    .userbox{
      background:#111c35;
      border:1px solid rgba(148,163,184,.25);
      border-radius:12px;
      padding:12px;
    }
    .userbox .name{font-weight:700}
    .userbox .role{font-size:13px;color:#cbd5e1}
    .menu{display:flex;flex-direction:column;gap:6px}
    .menu-item{
      display:flex;align-items:center;justify-content:space-between;
      color:#cbd5e1;text-decoration:none;
      padding:10px 12px;border-radius:10px;
      border:1px solid transparent;font-size:14px;
      cursor:pointer;
    }
    .menu-item.active{
      background:#e5e7eb;color:#0f172a;font-weight:700;border-color:#d1d5db;
    }
    .badge{
      display:inline-flex;align-items:center;justify-content:center;
      min-width:20px;height:20px;padding:0 8px;border-radius:999px;
      font-size:12px;font-weight:700;color:white;
    }
    .b-warning{background:var(--warning)}
    .main{flex:1;padding:20px}
    .topbar{
      display:flex;align-items:center;justify-content:space-between;
      margin-bottom:16px;
      background:var(--card);
      padding:12px 16px;border-radius:12px;box-shadow:var(--shadow);
    }
    .breadcrumbs{font-size:14px;color:var(--muted)}
    .top-right{display:flex;gap:12px;align-items:center}
    .icon-btn{
      position:relative;border:none;background:#eef2ff;border-radius:10px;padding:10px;cursor:pointer;
      color:#1e3a8a;font-weight:700;
    }
    .dot{
      position:absolute;top:5px;right:5px;width:8px;height:8px;border-radius:999px;background:#ef4444;
    }
    .avatar{
      width:38px;height:38px;border-radius:999px;background:#1d4ed8;color:#fff;
      display:flex;align-items:center;justify-content:center;font-weight:700;cursor:pointer;
    }
    .module{background:transparent}
    .card{
      background:var(--card);border-radius:var(--radius);box-shadow:var(--shadow);padding:16px;
    }
    .grid-4{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:12px}
    .grid-3{display:grid;grid-template-columns:2fr 1fr 1fr;gap:12px}
    .metric h3{margin:4px 0 0;font-size:26px}
    .metric small{color:var(--muted)}
    table{width:100%;border-collapse:collapse}
    th,td{padding:10px;border-bottom:1px solid #e5e7eb;text-align:left;font-size:14px}
    .status{font-size:12px;padding:6px 10px;border-radius:999px;color:#fff;font-weight:700}
    .s-confirmada{background:var(--success)}
    .s-aguardando{background:var(--warning)}
    .s-telemedicina{background:var(--info)}
    .s-cancelada{background:var(--danger)}
    .btn{
      border:none;border-radius:10px;padding:10px 14px;cursor:pointer;font-weight:700;
    }
    .btn-primary{background:var(--primary);color:#fff}
    .btn-primary:hover{background:var(--primary-2)}
    .btn-muted{background:#e5e7eb;color:#111827}
    .btn-danger{background:var(--danger);color:#fff}
    .btn-link{background:transparent;color:var(--primary);padding:0}
    .panel-list{display:flex;flex-direction:column;gap:10px}
    .panel-item{padding:10px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px}

    .login-wrap{
      min-height:100vh;display:grid;place-items:center;padding:16px;
      background:linear-gradient(135deg,#dbeafe,#e9d5ff);
    }
    .login-card{
      width:100%;max-width:460px;background:#fff;border-radius:16px;box-shadow:var(--shadow);padding:24px;
    }
    .title{margin:0 0 6px;font-size:26px}
    .subtitle{margin:0 0 16px;color:var(--muted)}
    .roles{display:flex;gap:8px;margin-bottom:14px}
    .role-btn{
      flex:1;padding:10px;border-radius:10px;border:1px solid #d1d5db;background:#fff;cursor:pointer;font-weight:700;
    }
    .role-btn.active{border-color:var(--primary);color:var(--primary);background:#eff6ff}
    label{font-size:13px;color:#374151;font-weight:600}
    input,select,textarea{
      width:100%;padding:10px 12px;border:1px solid #d1d5db;border-radius:10px;background:#fff;
      margin-top:6px;margin-bottom:10px;font:inherit;
    }
    textarea{min-height:90px;resize:vertical}
    .error-inline{font-size:12px;color:var(--danger);margin-top:-6px;margin-bottom:8px;display:none}
    .show{display:block}
    .stepper{display:flex;gap:8px;margin-bottom:16px}
    .step{
      flex:1;padding:10px;border-radius:10px;text-align:center;font-weight:700;
      background:#e5e7eb;color:#4b5563;
    }
    .step.active{background:#dbeafe;color:#1e40af}
    .step.done{background:#dcfce7;color:#166534}
    .calendar{display:grid;grid-template-columns:repeat(7,1fr);gap:8px}
    .day{
      padding:10px;border-radius:8px;text-align:center;border:1px solid #d1d5db;cursor:pointer;background:#fff
    }
    .day.available{background:#eff6ff;border-color:#93c5fd;color:#1d4ed8}
    .day.unavailable{background:#f3f4f6;color:#9ca3af;cursor:not-allowed}
    .day.selected{outline:2px solid #2563eb}
    .hours{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:8px;margin-top:12px}
    .hour{
      padding:9px;border-radius:8px;border:1px solid #d1d5db;text-align:center;cursor:pointer;background:#fff
    }
    .hour.blocked{text-decoration:line-through;color:#9ca3af;background:#f3f4f6;cursor:not-allowed}
    .hour.selected{background:#2563eb;color:#fff;border-color:#1d4ed8}
    .timeline{display:flex;flex-direction:column;gap:10px}
    .event{border-left:4px solid #d1d5db;padding:10px 12px;background:#fff;border-radius:8px}
    .t-consulta{border-color:#3b82f6}
    .t-retorno{border-color:#16a34a}
    .t-tele{border-color:#f59e0b}
    .t-exame{border-color:#9ca3af}
    .chip{display:inline-block;padding:4px 8px;border-radius:999px;font-size:12px;color:#fff;font-weight:700}
    .chip-red{background:#dc2626}.chip-orange{background:#f59e0b}.chip-blue{background:#0ea5e9}
    .checklist{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:8px}
    .call-room{display:grid;gap:12px}
    .timer{font-size:34px;font-weight:800;text-align:center}
    .toggles{display:flex;gap:8px;justify-content:center}
    .toggle-red{background:#ef4444;color:#fff}
    .toast-wrap{
      position:fixed;top:16px;right:16px;display:flex;flex-direction:column;gap:8px;z-index:1000;
    }
    .toast{
      color:#fff;padding:10px 14px;border-radius:10px;box-shadow:var(--shadow);font-weight:700;min-width:220px
    }
    .toast.success{background:var(--success)}
    .toast.error{background:var(--danger)}
    .toast.info{background:var(--info)}
    .row{display:flex;gap:10px;align-items:center;flex-wrap:wrap}
    .space{height:12px}
    @media (max-width:1100px){
      .grid-4{grid-template-columns:repeat(2,minmax(0,1fr))}
      .grid-3{grid-template-columns:1fr}
      .sidebar{width:220px}
    }
    @media (max-width:820px){
      .app{flex-direction:column}
      .sidebar{width:100%;height:auto;position:relative}
      .hours{grid-template-columns:repeat(2,minmax(0,1fr))}
      .checklist{grid-template-columns:1fr}
    }
  </style>
</head>
<body>
  <div id="loginView" class="login-wrap">
    <div class="login-card">
      <h1 class="title">SGHSS VidaPlus</h1>
      <p class="subtitle">Acesso ao sistema hospitalar inteligente</p>
      <div class="roles">
        <button class="role-btn active" data-role="paciente">Paciente</button>
        <button class="role-btn" data-role="medico">Médico</button>
        <button class="role-btn" data-role="admin">Admin</button>
      </div>
      <label for="email">Email</label>
      <input id="email" type="email" value="ana.souza@email.com" />
      <div id="emailError" class="error-inline">Email é obrigatório.</div>
      <label for="senha">Senha</label>
      <input id="senha" type="password" value="123456" />
      <div id="senhaError" class="error-inline">Senha deve ter ao menos 6 caracteres.</div>
      <button id="loginBtn" class="btn btn-primary" style="width:100%">Entrar</button>
    </div>
  </div>

  <div id="appView" class="app hidden">
    <aside class="sidebar">
      <div class="brand">VidaPlus SGHSS</div>
      <div class="userbox">
        <div id="sbName" class="name">Ana Souza</div>
        <div id="sbRole" class="role">Paciente</div>
      </div>
      <nav class="menu" id="menu"></nav>
    </aside>
    <main class="main">
      <header class="topbar">
        <div id="breadcrumb" class="breadcrumbs">Início / Dashboard</div>
        <div class="top-right">
          <button class="icon-btn" aria-label="Notificações">🔔<span class="dot"></span></button>
          <div id="avatar" class="avatar">AS</div>
        </div>
      </header>

      <section id="page-dashboard" class="module"></section>
      <section id="page-agendamento" class="module hidden"></section>
      <section id="page-pacientes" class="module hidden"></section>
      <section id="page-prontuario" class="module hidden"></section>
      <section id="page-telemedicina" class="module hidden"></section>
      <section id="page-lgpd" class="module hidden"></section>
    </main>
  </div>

  <div id="toasts" class="toast-wrap"></div>

  <script>
    const state = {
      currentRole: "paciente",
      currentPage: "dashboard",
      pacientes: [
        { id: 1, nome: "Ana Beatriz", cpf: "123.456.789-09", telefone: "(11) 98888-1001", idade: 32, sexo: "Feminino", sangue: "O+", alergias: ["Dipirona", "Latex"] },
        { id: 2, nome: "Carlos Menezes", cpf: "111.222.333-44", telefone: "(11) 97777-2002", idade: 47, sexo: "Masculino", sangue: "A-", alergias: [] },
        { id: 3, nome: "Paula Rios", cpf: "987.654.321-00", telefone: "(11) 96666-3003", idade: 28, sexo: "Feminino", sangue: "B+", alergias: ["Penicilina"] },
        { id: 4, nome: "Ricardo Alves", cpf: "222.333.444-55", telefone: "(11) 95555-4004", idade: 61, sexo: "Masculino", sangue: "AB+", alergias: [] }
      ],
      registros: [
        { tipo: "Consulta", data: "20/04/2026", medico: "Dra. Helena Cruz", descricao: "Avaliação clínica geral" },
        { tipo: "Retorno", data: "28/04/2026", medico: "Dr. Marcos Lima", descricao: "Ajuste de medicação anti-hipertensiva" },
        { tipo: "Telemedicina", data: "02/05/2026", medico: "Dra. Helena Cruz", descricao: "Acompanhamento remoto dos sintomas" }
      ],
      consultas: [
        { paciente: "Ana Beatriz", medico: "Dra. Helena Cruz", data: "05/05/2026 09:00", status: "Confirmada" },
        { paciente: "Carlos Menezes", medico: "Dr. Daniel Freitas", data: "05/05/2026 10:00", status: "Aguardando" },
        { paciente: "Paula Rios", medico: "Dra. Carla Mota", data: "05/05/2026 11:30", status: "Telemedicina" },
        { paciente: "Ricardo Alves", medico: "Dr. Marcos Lima", data: "05/05/2026 14:00", status: "Cancelada" }
      ],
      agData: { especialidade: "", medico: "", motivo: "" },
      selectedDate: "",
      selectedHour: "",
      callSeconds: 0,
      callInterval: null,
      agStep: 1,
      pendingBadge: 3,
      selectedPacienteId: 1
    };

    const roleMap = {
      paciente: { nome: "Ana Souza", cargo: "Paciente" },
      medico: { nome: "Dr. João Martins", cargo: "Médico" },
      admin: { nome: "Fernanda Costa", cargo: "Administrador" }
    };

    const doctorsBySpec = {
      "Cardiologia": ["Dr. Marcos Lima", "Dra. Helena Cruz"],
      "Clínico Geral": ["Dr. Daniel Freitas", "Dra. Carla Mota"],
      "Dermatologia": ["Dra. Patricia Dias", "Dr. Rafael Borges"],
      "Pediatria": ["Dra. Juliana Araujo", "Dr. Lucas Teles"]
    };

    const menuItems = [
      { key: "dashboard", label: "Dashboard" },
      { key: "agendamento", label: "Agendamento", badge: true },
      { key: "pacientes", label: "Cadastro Pacientes" },
      { key: "prontuario", label: "Prontuário Eletrônico" },
      { key: "telemedicina", label: "Telemedicina" },
      { key: "lgpd", label: "LGPD" }
    ];

    function toast(msg, type="info", duration=3000){
      const el = document.createElement("div");
      el.className = "toast " + type;
      el.textContent = msg;
      document.getElementById("toasts").appendChild(el);
      setTimeout(() => el.remove(), duration);
    }

    function initMenu(){
      const menu = document.getElementById("menu");
      menu.innerHTML = menuItems.map(item => `
        <a class="menu-item ${state.currentPage===item.key?"active":""}" data-page="${item.key}">
          <span>${item.label}</span>
          ${item.badge?`<span class="badge b-warning" id="pendingBadge">${state.pendingBadge}</span>`:""}
        </a>
      `).join("");
      menu.querySelectorAll(".menu-item").forEach(m => {
        m.addEventListener("click", () => navigate(m.dataset.page));
      });
    }

    function navigate(page){
      state.currentPage = page;
      document.querySelectorAll(".module").forEach(s => s.classList.add("hidden"));
      document.getElementById("page-" + page).classList.remove("hidden");
      initMenu();
      const names = {
        dashboard: "Dashboard",
        agendamento: "Agendamento",
        pacientes: "Cadastro Pacientes",
        prontuario: "Prontuário Eletrônico",
        telemedicina: "Telemedicina",
        lgpd: "LGPD"
      };
      document.getElementById("breadcrumb").textContent = `Início / ${names[page]}`;
      if(page==="dashboard") renderDashboard();
      if(page==="agendamento") renderAgendamento();
      if(page==="pacientes") renderPacientes();
      if(page==="prontuario") renderProntuario();
      if(page==="telemedicina") renderTelemedicina();
      if(page==="lgpd") renderLGPD();
    }

    function getStatusClass(status){
      return "s-" + status.toLowerCase();
    }

    function renderDashboard(){
      const el = document.getElementById("page-dashboard");
      el.innerHTML = `
        <div class="grid-4">
          <div class="card metric"><small>Consultas do dia</small><h3>34</h3></div>
          <div class="card metric"><small>Pacientes ativos</small><h3>1248</h3></div>
          <div class="card metric"><small>Internados</small><h3>17</h3></div>
          <div class="card metric"><small>Exames pendentes</small><h3>52</h3></div>
        </div>
        <div class="space"></div>
        <div class="grid-3">
          <div class="card">
            <h3>Próximas Consultas</h3>
            <table>
              <thead><tr><th>Paciente</th><th>Médico</th><th>Data</th><th>Status</th><th>Ação</th></tr></thead>
              <tbody>
                ${state.consultas.slice(0,4).map((c,idx)=>`
                  <tr>
                    <td>${c.paciente}</td>
                    <td>${c.medico}</td>
                    <td>${c.data}</td>
                    <td><span class="status ${getStatusClass(c.status)}">${c.status}</span></td>
                    <td><button class="btn btn-link ver-consulta" data-idx="${idx}">Ver em consulta</button></td>
                  </tr>
                `).join("")}
              </tbody>
            </table>
          </div>
          <div class="card">
            <h3>Acesso rápido</h3>
            <div class="panel-list">
              <button class="btn btn-primary atalho" data-go="agendamento">Novo agendamento</button>
              <button class="btn btn-primary atalho" data-go="pacientes">Cadastrar paciente</button>
              <button class="btn btn-primary atalho" data-go="telemedicina">Abrir teleconsulta</button>
            </div>
          </div>
          <div class="card">
            <h3>Alertas</h3>
            <div class="panel-list">
              <div class="panel-item">Exame crítico pendente para 3 pacientes.</div>
              <div class="panel-item">2 consultas aguardando confirmação.</div>
              <div class="panel-item">Atualização LGPD disponível.</div>
            </div>
          </div>
        </div>
      `;
      el.querySelectorAll(".ver-consulta").forEach(btn => btn.onclick = () => toast("Abrindo detalhes da consulta...", "info"));
      el.querySelectorAll(".atalho").forEach(btn => btn.onclick = () => navigate(btn.dataset.go));
    }

    function renderAgendamento(){
      const el = document.getElementById("page-agendamento");
      const steps = `
        <div class="stepper">
          <div class="step ${state.agStep===1?"active":state.agStep>1?"done":""}">1. Dados</div>
          <div class="step ${state.agStep===2?"active":state.agStep>2?"done":""}">2. Data/Hora</div>
          <div class="step ${state.agStep===3?"active":""}">3. Confirmação</div>
        </div>`;

      if(state.agStep===1){
        const doctors = doctorsBySpec[state.agData.especialidade] || [];
        el.innerHTML = `
          <div class="card">${steps}
            <label>Especialidade</label>
            <select id="agEspecialidade">
              <option value="">Selecione</option>
              ${Object.keys(doctorsBySpec).map(s=>`<option ${state.agData.especialidade===s?"selected":""}>${s}</option>`).join("")}
            </select>
            <div id="agEspErr" class="error-inline">Especialidade é obrigatória.</div>
            <label>Médico</label>
            <select id="agMedico">
              <option value="">Selecione</option>
              ${doctors.map(m=>`<option ${state.agData.medico===m?"selected":""}>${m}</option>`).join("")}
            </select>
            <div id="agMedErr" class="error-inline">Médico é obrigatório.</div>
            <label>Motivo</label>
            <textarea id="agMotivo" placeholder="Descreva o motivo da consulta">${state.agData.motivo||""}</textarea>
            <div id="agMotErr" class="error-inline">Motivo é obrigatório.</div>
            <div class="row">
              <button id="next1" class="btn btn-primary">Próximo</button>
            </div>
          </div>
        `;
        document.getElementById("agEspecialidade").onchange = (e) => {
          state.agData.especialidade = e.target.value;
          state.agData.medico = "";
          renderAgendamento();
        };
        document.getElementById("agMedico").onchange = (e)=> state.agData.medico = e.target.value;
        document.getElementById("agMotivo").oninput = (e)=> state.agData.motivo = e.target.value;
        document.getElementById("next1").onclick = () => {
          let ok = true;
          const showErr = (id, cond) => document.getElementById(id).classList.toggle("show", cond);
          showErr("agEspErr", !state.agData.especialidade); if(!state.agData.especialidade) ok = false;
          showErr("agMedErr", !state.agData.medico); if(!state.agData.medico) ok = false;
          showErr("agMotErr", !state.agData.motivo.trim()); if(!state.agData.motivo.trim()) ok = false;
          if(ok){state.agStep = 2; renderAgendamento();}
        };
      } else if(state.agStep===2){
        const days = [
          {d:"06/05", a:true},{d:"07/05", a:false},{d:"08/05", a:true},{d:"09/05", a:false},
          {d:"10/05", a:true},{d:"11/05", a:true},{d:"12/05", a:false}
        ];
        const slots = [
          {h:"08:00",free:true},{h:"09:00",free:false},{h:"10:00",free:true},{h:"11:00",free:false},
          {h:"13:00",free:true},{h:"14:00",free:true},{h:"15:00",free:false},{h:"16:00",free:true}
        ];
        el.innerHTML = `
          <div class="card">${steps}
            <h3>Selecione data e horário</h3>
            <div class="calendar">
              ${days.map(day=>`<div class="day ${day.a?"available":"unavailable"} ${state.selectedDate===day.d?"selected":""}" data-date="${day.d}" data-available="${day.a}">${day.d}</div>`).join("")}
            </div>
            <div class="hours">
              ${slots.map(slot=>`<div class="hour ${slot.free?"":"blocked"} ${state.selectedHour===slot.h?"selected":""}" data-hour="${slot.h}" data-free="${slot.free}">${slot.h}</div>`).join("")}
            </div>
            <div id="agDataErr" class="error-inline">Selecione uma data disponível e um horário livre.</div>
            <div class="row">
              <button id="back2" class="btn btn-muted">Voltar</button>
              <button id="next2" class="btn btn-primary">Próximo</button>
            </div>
          </div>
        `;
        el.querySelectorAll(".day").forEach(d => d.onclick = () => {
          if(d.dataset.available==="true"){state.selectedDate = d.dataset.date; renderAgendamento();}
        });
        el.querySelectorAll(".hour").forEach(h => h.onclick = () => {
          if(h.dataset.free==="true"){state.selectedHour = h.dataset.hour; renderAgendamento();}
        });
        document.getElementById("back2").onclick = () => {state.agStep=1; renderAgendamento();};
        document.getElementById("next2").onclick = () => {
          const ok = !!(state.selectedDate && state.selectedHour);
          document.getElementById("agDataErr").classList.toggle("show", !ok);
          if(ok){state.agStep=3; renderAgendamento();}
        };
      } else {
        el.innerHTML = `
          <div class="card">${steps}
            <h3>Resumo da consulta</h3>
            <p><b>Especialidade:</b> ${state.agData.especialidade}</p>
            <p><b>Médico:</b> ${state.agData.medico}</p>
            <p><b>Motivo:</b> ${state.agData.motivo}</p>
            <p><b>Data:</b> ${state.selectedDate} às ${state.selectedHour}</p>
            <div class="row">
              <button id="back3" class="btn btn-muted">Voltar</button>
              <button id="confirmAg" class="btn btn-primary">Confirmar Agendamento</button>
            </div>
          </div>
        `;
        document.getElementById("back3").onclick = () => {state.agStep=2; renderAgendamento();};
        document.getElementById("confirmAg").onclick = () => {
          state.consultas.unshift({
            paciente: roleMap[state.currentRole].nome,
            medico: state.agData.medico,
            data: `${state.selectedDate}/2026 ${state.selectedHour}`,
            status: "Confirmada"
          });
          state.pendingBadge += 1;
          el.innerHTML = `
            <div class="card" style="text-align:center">
              <div style="font-size:48px;color:#16a34a">✔</div>
              <h2>Agendamento confirmado com sucesso!</h2>
              <p>Sua consulta foi registrada e adicionada ao dashboard.</p>
              <button class="btn btn-primary" id="goDash">Ir para Dashboard</button>
            </div>
          `;
          toast("Consulta confirmada com sucesso!", "success", 4000);
          document.getElementById("goDash").onclick = () => {
            state.agStep = 1;
            navigate("dashboard");
          };
          initMenu();
        };
      }
    }

    function cpfMask(v){
      v=v.replace(/\D/g,"").slice(0,11);
      return v.replace(/(\d{3})(\d)/,"$1.$2").replace(/(\d{3})(\d)/,"$1.$2").replace(/(\d{3})(\d{1,2})$/,"$1-$2");
    }
    function phoneMask(v){
      v=v.replace(/\D/g,"").slice(0,11);
      return v.replace(/(\d{2})(\d)/,"($1) $2").replace(/(\d{5})(\d)/,"$1-$2");
    }
    function validateCPF(cpf){
      cpf = cpf.replace(/\D/g,"");
      if(cpf.length!==11 || /^(\d)\1+$/.test(cpf)) return false;
      let sum = 0;
      for(let i=0;i<9;i++) sum += Number(cpf[i])*(10-i);
      let d1 = (sum*10)%11; if(d1===10) d1=0;
      if(d1!==Number(cpf[9])) return false;
      sum = 0;
      for(let i=0;i<10;i++) sum += Number(cpf[i])*(11-i);
      let d2 = (sum*10)%11; if(d2===10) d2=0;
      return d2===Number(cpf[10]);
    }

    function renderPacientes(){
      const el = document.getElementById("page-pacientes");
      el.innerHTML = `
        <div class="card">
          <div class="row" style="justify-content:space-between">
            <h3 style="margin:0">Pacientes</h3>
            <button id="novoPaciente" class="btn btn-primary">Novo Paciente</button>
          </div>
          <input id="buscaPaciente" placeholder="Buscar por nome ou CPF..." />
          <div id="formNovo" class="hidden card" style="margin-bottom:10px;background:#f8fafc">
            <h4>Novo Paciente</h4>
            <label>Nome</label><input id="pNome" />
            <div id="pNomeErr" class="error-inline">Nome é obrigatório.</div>
            <label>CPF</label><input id="pCpf" />
            <div id="pCpfErr" class="error-inline">CPF inválido.</div>
            <label>Telefone</label><input id="pFone" />
            <div class="row">
              <button id="salvarPaciente" class="btn btn-primary">Salvar</button>
              <button id="cancelarPaciente" class="btn btn-muted">Cancelar</button>
            </div>
          </div>
          <table>
            <thead><tr><th>Nome</th><th>CPF</th><th>Telefone</th><th>Ação</th></tr></thead>
            <tbody id="pacRows"></tbody>
          </table>
        </div>
      `;
      const renderRows = (term="") => {
        const t = term.toLowerCase();
        const rows = state.pacientes.filter(p => p.nome.toLowerCase().includes(t) || p.cpf.includes(term));
        document.getElementById("pacRows").innerHTML = rows.map(p=>`
          <tr>
            <td>${p.nome}</td><td>${p.cpf}</td><td>${p.telefone}</td>
            <td><button class="btn btn-link prontuario-btn" data-id="${p.id}">Prontuário</button></td>
          </tr>
        `).join("");
        document.querySelectorAll(".prontuario-btn").forEach(b => b.onclick = () => {
          state.selectedPacienteId = Number(b.dataset.id);
          navigate("prontuario");
        });
      };
      renderRows();
      document.getElementById("buscaPaciente").oninput = (e) => renderRows(e.target.value);
      document.getElementById("novoPaciente").onclick = () => document.getElementById("formNovo").classList.remove("hidden");
      document.getElementById("cancelarPaciente").onclick = () => document.getElementById("formNovo").classList.add("hidden");
      document.getElementById("pCpf").oninput = (e) => e.target.value = cpfMask(e.target.value);
      document.getElementById("pFone").oninput = (e) => e.target.value = phoneMask(e.target.value);
      document.getElementById("salvarPaciente").onclick = () => {
        const nome = document.getElementById("pNome").value.trim();
        const cpf = document.getElementById("pCpf").value.trim();
        const fone = document.getElementById("pFone").value.trim();
        const nomeOk = !!nome;
        const cpfOk = validateCPF(cpf);
        document.getElementById("pNomeErr").classList.toggle("show", !nomeOk);
        document.getElementById("pCpfErr").classList.toggle("show", !cpfOk);
        if(!nomeOk || !cpfOk) return;
        state.pacientes.push({ id: Date.now(), nome, cpf, telefone: fone, idade: 0, sexo: "-", sangue: "-", alergias: [] });
        toast("Paciente cadastrado com sucesso.", "success");
        document.getElementById("formNovo").classList.add("hidden");
        renderPacientes();
      };
    }

    function renderProntuario(){
      const el = document.getElementById("page-prontuario");
      const p = state.pacientes.find(x => x.id===state.selectedPacienteId) || state.pacientes[0];
      const initials = p.nome.split(" ").map(n=>n[0]).slice(0,2).join("").toUpperCase();
      el.innerHTML = `
        <div class="grid-3">
          <div class="card">
            <div class="row">
              <div class="avatar">${initials}</div>
              <div><h3 style="margin:0">${p.nome}</h3><small>${p.idade} anos • ${p.sexo}</small></div>
            </div>
            <p><b>Tipo sanguíneo:</b> ${p.sangue}</p>
            <p><b>Alergias:</b>
              <span class="chip chip-red">Dipirona</span>
              <span class="chip chip-orange">Latex</span>
            </p>
            <div class="row">
              <div class="panel-item">Consultas: <b>12</b></div>
              <div class="panel-item">Exames: <b>7</b></div>
            </div>
          </div>
          <div class="card" style="grid-column:span 2">
            <h3>Timeline clínica</h3>
            <div class="timeline">
              ${state.registros.map(r=>`
                <div class="event ${r.tipo==="Consulta"?"t-consulta":r.tipo==="Retorno"?"t-retorno":r.tipo==="Telemedicina"?"t-tele":"t-exame"}">
                  <b>${r.tipo}</b> • ${r.data} • ${r.medico}<br>${r.descricao}
                </div>
              `).join("")}
            </div>
          </div>
        </div>
        <div class="space"></div>
        <div class="card">
          <h3>Novo registro</h3>
          <div class="row">
            <div style="flex:1">
              <label>Tipo</label>
              <select id="rTipo">
                <option>Consulta</option><option>Retorno</option><option>Telemedicina</option><option>Exame</option>
              </select>
            </div>
            <div style="flex:1">
              <label>Médico</label><input id="rMedico" />
              <div id="rMedErr" class="error-inline">Médico é obrigatório.</div>
            </div>
          </div>
          <label>Descrição</label><textarea id="rDesc"></textarea>
          <div id="rDescErr" class="error-inline">Descrição é obrigatória.</div>
          <button id="addRegistro" class="btn btn-primary">Adicionar registro</button>
        </div>
      `;
      document.getElementById("addRegistro").onclick = () => {
        const tipo = document.getElementById("rTipo").value;
        const medico = document.getElementById("rMedico").value.trim();
        const descricao = document.getElementById("rDesc").value.trim();
        document.getElementById("rMedErr").classList.toggle("show", !medico);
        document.getElementById("rDescErr").classList.toggle("show", !descricao);
        if(!medico || !descricao) return;
        state.registros.unshift({ tipo, data: new Date().toLocaleDateString("pt-BR"), medico, descricao });
        toast("Registro adicionado ao prontuário.", "success");
        renderProntuario();
      };
    }

    function formatTimer(sec){
      const m = String(Math.floor(sec/60)).padStart(2,"0");
      const s = String(sec%60).padStart(2,"0");
      return `${m}:${s}`;
    }

    function renderTelemedicina(inRoom=false){
      const el = document.getElementById("page-telemedicina");
      if(!inRoom){
        el.innerHTML = `
          <div class="card">
            <h3>Consulta agendada</h3>
            <p><b>Médico:</b> Dra. Helena Cruz</p>
            <p><b>Especialidade:</b> Clínico Geral</p>
            <p><span class="chip chip-blue">Hoje 15:00</span></p>
            <h4>Checklist pré-consulta (<span id="ckCount">0</span>/4)</h4>
            <div class="checklist">
              <label><input type="checkbox" class="ck" /> Internet estável</label>
              <label><input type="checkbox" class="ck" /> Câmera funcionando</label>
              <label><input type="checkbox" class="ck" /> Microfone funcionando</label>
              <label><input type="checkbox" class="ck" /> Documento em mãos</label>
            </div>
            <div class="space"></div>
            <div class="row">
              <button id="receitaAtiva" class="btn btn-primary">Baixar receita</button>
              <button class="btn btn-muted" disabled>Receita expirada</button>
            </div>
            <div class="space"></div>
            <button id="entrarSala" class="btn btn-primary">Entrar na Sala</button>
          </div>
        `;
        const cks = el.querySelectorAll(".ck");
        const update = () => document.getElementById("ckCount").textContent = [...cks].filter(c=>c.checked).length;
        cks.forEach(c => c.onchange = update);
        document.getElementById("receitaAtiva").onclick = () => toast("Download da receita iniciado.", "info");
        document.getElementById("entrarSala").onclick = () => {
          state.callSeconds = 0;
          renderTelemedicina(true);
        };
      } else {
        el.innerHTML = `
          <div class="card call-room">
            <h3>Sala de Teleconsulta</h3>
            <div id="timer" class="timer">${formatTimer(state.callSeconds)}</div>
            <div class="toggles">
              <button id="micBtn" class="btn btn-muted">Mic</button>
              <button id="camBtn" class="btn btn-muted">Cam</button>
              <button id="chatBtn" class="btn btn-primary">Chat</button>
            </div>
            <button id="encerrarBtn" class="btn btn-danger">Encerrar consulta</button>
          </div>
        `;
        let micOn = false, camOn = false;
        const micBtn = document.getElementById("micBtn");
        const camBtn = document.getElementById("camBtn");
        micBtn.onclick = () => { micOn = !micOn; micBtn.classList.toggle("toggle-red", micOn); };
        camBtn.onclick = () => { camOn = !camOn; camBtn.classList.toggle("toggle-red", camOn); };
        document.getElementById("chatBtn").onclick = () => toast("Chat em breve.", "info");
        if(state.callInterval) clearInterval(state.callInterval);
        state.callInterval = setInterval(() => {
          state.callSeconds++;
          const t = document.getElementById("timer");
          if(t) t.textContent = formatTimer(state.callSeconds);
        }, 1000);
        document.getElementById("encerrarBtn").onclick = () => {
          clearInterval(state.callInterval);
          state.callInterval = null;
          const dur = formatTimer(state.callSeconds);
          renderTelemedicina(false);
          toast(`Consulta encerrada. Duração: ${dur}.`, "info");
        };
      }
    }

    function renderLGPD(){
      const el = document.getElementById("page-lgpd");
      const consents = [
        { id:1, finalidade:"Atendimento clínico", base:"Execução de políticas públicas", data:"03/05/2026", status:"Ativo" },
        { id:2, finalidade:"Telemonitoramento", base:"Consentimento do titular", data:"01/05/2026", status:"Ativo" },
        { id:3, finalidade:"Compartilhamento laboratorial", base:"Proteção da vida", data:"28/04/2026", status:"Ativo" }
      ];
      el.innerHTML = `
        <div class="card">
          <h3>Consentimentos</h3>
          <table>
            <thead><tr><th>Finalidade</th><th>Base legal</th><th>Data</th><th>Status</th><th>Ação</th></tr></thead>
            <tbody>
              ${consents.map(c=>`
                <tr>
                  <td>${c.finalidade}</td><td>${c.base}</td><td>${c.data}</td>
                  <td><span class="status ${c.status==="Ativo"?"s-confirmada":"s-cancelada"}" id="st-${c.id}">${c.status}</span></td>
                  <td><button class="btn btn-link revogar" data-id="${c.id}">Revogar</button> <a href="#" id="lk-${c.id}">ver detalhes</a></td>
                </tr>
              `).join("")}
            </tbody>
          </table>
        </div>
        <div class="space"></div>
        <div class="card">
          <h3>Log de acessos</h3>
          <table>
            <thead><tr><th>Médico</th><th>Ação</th><th>Horário</th></tr></thead>
            <tbody>
              <tr><td>Dra. Helena Cruz</td><td>Visualizou prontuário</td><td>04/05/2026 09:12</td></tr>
              <tr><td>Dr. Marcos Lima</td><td>Atualizou prescrição</td><td>04/05/2026 10:04</td></tr>
              <tr><td>Dra. Carla Mota</td><td>Solicitou exame</td><td>04/05/2026 11:27</td></tr>
            </tbody>
          </table>
        </div>
        <div class="space"></div>
        <div class="card">
          <h3>Direitos do titular</h3>
          <div class="row">
            <button id="expDados" class="btn btn-primary">Exportar dados</button>
            <button id="corrDados" class="btn btn-muted">Corrigir dados</button>
            <button id="excDados" class="btn btn-danger">Solicitar exclusão</button>
          </div>
        </div>
      `;
      el.querySelectorAll(".revogar").forEach(b => b.onclick = () => {
        const id = b.dataset.id;
        document.getElementById("st-" + id).textContent = "Revogado";
        document.getElementById("st-" + id).className = "status s-cancelada";
        const lk = document.getElementById("lk-" + id);
        if(lk) lk.remove();
        b.remove();
      });
      document.getElementById("expDados").onclick = () => toast("Solicitação enviada ao DPO para exportação dos dados.", "info");
      document.getElementById("corrDados").onclick = () => toast("Fluxo de correção de dados iniciado.", "info");
      document.getElementById("excDados").onclick = () => toast("Solicitação de exclusão enviada ao DPO.", "error");
    }

    function initLogin(){
      document.querySelectorAll(".role-btn").forEach(btn => btn.addEventListener("click", () => {
        document.querySelectorAll(".role-btn").forEach(b=>b.classList.remove("active"));
        btn.classList.add("active");
        state.currentRole = btn.dataset.role;
      }));
      document.getElementById("loginBtn").onclick = () => {
        const email = document.getElementById("email").value.trim();
        const senha = document.getElementById("senha").value.trim();
        const eErr = document.getElementById("emailError");
        const sErr = document.getElementById("senhaError");
        const emailBad = !email;
        const passBad = senha.length < 6;
        eErr.classList.toggle("show", emailBad);
        sErr.classList.toggle("show", passBad);
        if(emailBad || passBad) return;
        document.getElementById("loginView").classList.add("hidden");
        document.getElementById("appView").classList.remove("hidden");
        const usr = roleMap[state.currentRole];
        document.getElementById("sbName").textContent = usr.nome;
        document.getElementById("sbRole").textContent = usr.cargo;
        document.getElementById("avatar").textContent = usr.nome.split(" ").map(v=>v[0]).slice(0,2).join("").toUpperCase();
        toast(`Bem-vindo(a), ${usr.nome}!`, "success");
        initMenu();
        navigate("dashboard");
      };
      document.getElementById("avatar").onclick = () => toast("Abrindo configurações do perfil.", "info");
    }

    initLogin();
  </script>
</body>
</html>