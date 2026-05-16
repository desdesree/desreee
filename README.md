# desreee
Desree's Personal Website

<style>
  :root {
    --g-green: #4a7c59;
    --g-light: #c8dfc8;
    --g-pale: #e8f2e8;
    --g-dark: #2d5016;
    --g-bark: #7a5c3a;
    --g-sky: #b8d4e8;
    --g-cream: #f5f0e8;
    --g-text: #2d3a2d;
    --g-muted: #6b8f6b;
    --g-leaf: #639922;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: var(--font-sans); }
  .dash { padding: 1.5rem 1rem; max-width: 680px; }

  .quote-bar {
    background: var(--g-pale);
    border: 0.5px solid var(--g-light);
    border-radius: 12px;
    padding: 1rem 1.25rem;
    margin-bottom: 1.25rem;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .quote-leaf { font-size: 22px; flex-shrink: 0; }
  .quote-text { font-size: 14px; color: var(--g-dark); font-style: italic; line-height: 1.5; flex: 1; }
  .quote-author { font-size: 12px; color: var(--g-muted); margin-top: 2px; }

  .section-label {
    font-size: 11px;
    font-weight: 500;
    color: var(--g-muted);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .add-row {
    display: flex;
    gap: 8px;
    margin-bottom: 1rem;
  }
  .add-row input, .add-row select {
    flex: 1;
    background: var(--g-pale);
    border: 0.5px solid var(--g-light);
    border-radius: 8px;
    padding: 8px 10px;
    font-size: 13px;
    color: var(--g-text);
    outline: none;
  }
  .add-row input:focus, .add-row select:focus {
    border-color: var(--g-green);
  }
  .add-row input[type="date"] { flex: 0.8; }
  .add-btn {
    background: var(--g-green);
    color: #fff;
    border: none;
    border-radius: 8px;
    padding: 8px 14px;
    font-size: 13px;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 6px;
    white-space: nowrap;
    flex-shrink: 0;
  }
  .add-btn:hover { background: var(--g-dark); }

  .deadline-list { display: flex; flex-direction: column; gap: 8px; }
  .deadline-card {
    background: var(--g-pale);
    border: 0.5px solid var(--g-light);
    border-radius: 10px;
    padding: 10px 14px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .deadline-card.urgent { border-left: 3px solid #c0392b; background: #fdf5f4; }
  .deadline-card.soon { border-left: 3px solid var(--g-bark); background: #fdf8f2; }
  .deadline-card.ok { border-left: 3px solid var(--g-leaf); }

  .dl-dot {
    width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0;
  }
  .urgent .dl-dot { background: #c0392b; }
  .soon .dl-dot { background: var(--g-bark); }
  .ok .dl-dot { background: var(--g-leaf); }

  .dl-title { font-size: 14px; font-weight: 500; color: var(--g-text); flex: 1; }
  .dl-tag {
    font-size: 11px;
    background: var(--g-light);
    color: var(--g-dark);
    border-radius: 20px;
    padding: 2px 8px;
  }
  .dl-date { font-size: 12px; color: var(--g-muted); white-space: nowrap; }
  .dl-days { font-size: 11px; font-weight: 500; padding: 2px 7px; border-radius: 20px; }
  .urgent .dl-days { background: #fde8e6; color: #c0392b; }
  .soon .dl-days { background: #fdf0e0; color: var(--g-bark); }
  .ok .dl-days { background: var(--g-pale); color: var(--g-leaf); }
  .dl-del { background: none; border: none; color: var(--g-muted); cursor: pointer; font-size: 16px; padding: 2px; border-radius: 4px; }
  .dl-del:hover { color: #c0392b; background: #fde8e6; }

  .gcal-banner {
    margin-top: 1.25rem;
    background: var(--g-pale);
    border: 0.5px dashed var(--g-light);
    border-radius: 10px;
    padding: 12px 1rem;
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 13px;
    color: var(--g-muted);
  }
  .gcal-btn {
    margin-left: auto;
    background: var(--g-green);
    color: #fff;
    border: none;
    border-radius: 7px;
    padding: 6px 12px;
    font-size: 12px;
    cursor: pointer;
    white-space: nowrap;
  }
  .gcal-btn:hover { background: var(--g-dark); }

  .empty-state {
    text-align: center;
    padding: 2rem 1rem;
    color: var(--g-muted);
    font-size: 13px;
  }
  .filter-row {
    display: flex;
    gap: 6px;
    margin-bottom: 0.75rem;
    flex-wrap: wrap;
  }
  .filter-btn {
    background: none;
    border: 0.5px solid var(--g-light);
    border-radius: 20px;
    padding: 4px 12px;
    font-size: 12px;
    color: var(--g-muted);
    cursor: pointer;
  }
  .filter-btn.active {
    background: var(--g-green);
    color: #fff;
    border-color: var(--g-green);
  }
</style>

<div class="dash">
  <h2 class="sr-only">Studio Ghibli deadline dashboard with inspirational quotes</h2>

  <div class="quote-bar" id="quoteBar">
    <div class="quote-leaf" aria-hidden="true">🌿</div>
    <div>
      <div class="quote-text" id="quoteText">"Always believe that something wonderful is about to happen."</div>
      <div class="quote-author" id="quoteAuthor">— Anonymous</div>
    </div>
    <button onclick="nextQuote()" style="background:none;border:0.5px solid var(--g-light);border-radius:7px;padding:4px 10px;font-size:12px;color:var(--g-muted);cursor:pointer;" title="New quote"><i class="ti ti-refresh" aria-label="next quote"></i></button>
  </div>

  <div class="section-label">Add deadline</div>
  <div class="add-row">
    <input type="text" id="dlTitle" placeholder="Deadline name…" />
    <input type="date" id="dlDate" />
    <select id="dlTag">
      <option value="Work">Work</option>
      <option value="School">School</option>
      <option value="Personal">Personal</option>
      <option value="Project">Project</option>
      <option value="Health">Health</option>
    </select>
    <button class="add-btn" onclick="addDeadline()"><i class="ti ti-plus" aria-hidden="true"></i> Add</button>
  </div>

  <div style="display:flex; align-items:center; justify-content:space-between; margin-bottom:8px;">
    <div class="section-label" style="margin-bottom:0;">Upcoming deadlines</div>
    <div class="filter-row" style="margin-bottom:0;">
      <button class="filter-btn active" onclick="setFilter('all', this)">All</button>
      <button class="filter-btn" onclick="setFilter('Work', this)">Work</button>
      <button class="filter-btn" onclick="setFilter('School', this)">School</button>
      <button class="filter-btn" onclick="setFilter('Personal', this)">Personal</button>
    </div>
  </div>

  <div class="deadline-list" id="deadlineList"></div>

  <div class="gcal-banner">
    <i class="ti ti-calendar" style="font-size:18px;color:var(--g-green);" aria-hidden="true"></i>
    <span>Connect Google Calendar to sync deadlines automatically</span>
    <button class="gcal-btn" onclick="sendPrompt('How do I connect this dashboard to my Google Calendar?')">Connect ↗</button>
  </div>
</div>

<script>
const quotes = [
  { text: "Always believe that something wonderful is about to happen.", author: "Anonymous" },
  { text: "The world is full of magic things, patiently waiting for our senses to grow sharper.", author: "W.B. Yeats" },
  { text: "In every walk with nature, one receives far more than he seeks.", author: "John Muir" },
  { text: "It's the possibility of having a dream come true that makes life interesting.", author: "Paulo Coelho" },
  { text: "Do your best and let the rest go. You can't be perfect.", author: "Dan Millman" },
  { text: "You are braver than you believe, stronger than you seem, smarter than you think.", author: "A.A. Milne" },
  { text: "The secret of getting ahead is getting started.", author: "Mark Twain" },
  { text: "Even the darkest night will end and the sun will rise.", author: "Victor Hugo" },
];
let qIdx = Math.floor(Math.random() * quotes.length);

function nextQuote() {
  qIdx = (qIdx + 1) % quotes.length;
  document.getElementById('quoteText').textContent = '"' + quotes[qIdx].text + '"';
  document.getElementById('quoteAuthor').textContent = '— ' + quotes[qIdx].author;
}

let deadlines = [
  { id: 1, title: "Submit project proposal", date: offsetDate(3), tag: "Work" },
  { id: 2, title: "Final essay draft", date: offsetDate(7), tag: "School" },
  { id: 3, title: "Doctor appointment", date: offsetDate(14), tag: "Health" },
];
let nextId = 4;
let activeFilter = 'all';

function offsetDate(days) {
  const d = new Date();
  d.setDate(d.getDate() + days);
  return d.toISOString().split('T')[0];
}

function daysUntil(dateStr) {
  const today = new Date(); today.setHours(0,0,0,0);
  const d = new Date(dateStr + 'T00:00:00');
  return Math.round((d - today) / 86400000);
}

function urgency(days) {
  if (days <= 2) return 'urgent';
  if (days <= 7) return 'soon';
  return 'ok';
}

function daysLabel(days) {
  if (days < 0) return 'Overdue';
  if (days === 0) return 'Today';
  if (days === 1) return '1 day';
  return days + ' days';
}

function renderList() {
  const list = document.getElementById('deadlineList');
  let items = [...deadlines].sort((a,b) => a.date.localeCompare(b.date));
  if (activeFilter !== 'all') items = items.filter(d => d.tag === activeFilter);
  if (items.length === 0) {
    list.innerHTML = '<div class="empty-state">🌱 No deadlines yet — add one above!</div>';
    return;
  }
  list.innerHTML = items.map(d => {
    const days = daysUntil(d.date);
    const urg = urgency(days);
    const fmt = new Date(d.date + 'T00:00:00').toLocaleDateString('en-CA', {month:'short', day:'numeric'});
    return `<div class="deadline-card ${urg}">
      <div class="dl-dot"></div>
      <div class="dl-title">${d.title}</div>
      <span class="dl-tag">${d.tag}</span>
      <span class="dl-date">${fmt}</span>
      <span class="dl-days">${daysLabel(days)}</span>
      <button class="dl-del" onclick="removeDeadline(${d.id})" aria-label="Remove"><i class="ti ti-x"></i></button>
    </div>`;
  }).join('');
}

function addDeadline() {
  const title = document.getElementById('dlTitle').value.trim();
  const date = document.getElementById('dlDate').value;
  const tag = document.getElementById('dlTag').value;
  if (!title || !date) return;
  deadlines.push({ id: nextId++, title, date, tag });
  document.getElementById('dlTitle').value = '';
  document.getElementById('dlDate').value = '';
  renderList();
}

function removeDeadline(id) {
  deadlines = deadlines.filter(d => d.id !== id);
  renderList();
}

function setFilter(val, btn) {
  activeFilter = val;
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderList();
}

document.getElementById('dlTitle').addEventListener('keydown', e => {
  if (e.key === 'Enter') addDeadline();
});

renderList();
</script>
