# 🛡️ PACE 111 // DAACS & Lessons Learned
> **Course:** PACE 111: Program and Career Exploration | **Section:** 2265  
> **Degree Path:** Cyber Operations | **Term:** Summer 2026

---

<style>
/* ── Hacker Matrix Styling ── */
.daacs-container {
  font-family: 'Fira Code', monospace;
  color: #c8ffc8;
  background: rgba(0, 12, 4, 0.85);
  border: 1px solid rgba(0, 204, 51, 0.3);
  border-radius: 8px;
  padding: 20px;
  margin-top: 15px;
  box-shadow: 0 0 25px rgba(0, 204, 51, 0.1);
}

.daacs-nav-btn {
  background: rgba(0, 40, 12, 0.7);
  color: #7abf7a;
  border: 1px solid rgba(0, 204, 51, 0.25);
  padding: 8px 14px;
  border-radius: 6px;
  cursor: pointer;
  font-family: 'Fira Code', monospace;
  font-size: 0.78rem;
  transition: all 0.2s ease;
  margin: 3px;
}

.daacs-nav-btn:hover, .daacs-nav-btn.active {
  background: rgba(0, 204, 51, 0.25);
  color: #00ff41;
  border-color: #00ff41;
  box-shadow: 0 0 10px rgba(0, 255, 65, 0.4);
  transform: translateY(-1px);
}

.unit-card {
  background: rgba(0, 20, 6, 0.9);
  border: 1px solid rgba(0, 204, 51, 0.2);
  border-radius: 6px;
  padding: 18px;
  margin-bottom: 16px;
  transition: border-color 0.2s, box-shadow 0.2s;
}

.unit-card:hover {
  border-color: rgba(0, 255, 65, 0.5);
  box-shadow: 0 0 15px rgba(0, 204, 51, 0.15);
}

.unit-badge {
  display: inline-block;
  background: rgba(0, 204, 51, 0.15);
  color: #00ff41;
  border: 1px solid rgba(0, 204, 51, 0.4);
  padding: 2px 8px;
  border-radius: 4px;
  font-size: 0.72rem;
  margin-bottom: 8px;
  font-weight: bold;
}

.metric-bar-bg {
  background: rgba(0, 30, 10, 0.8);
  border: 1px solid rgba(0, 204, 51, 0.2);
  height: 20px;
  border-radius: 10px;
  overflow: hidden;
  margin: 6px 0 12px 0;
}

.metric-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #008822, #00ff41);
  transition: width 0.6s ease;
  box-shadow: 0 0 10px rgba(0, 255, 65, 0.6);
}

.tracker-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  border-bottom: 1px solid rgba(0, 204, 51, 0.1);
  font-size: 0.85rem;
}

.tracker-item:hover {
  background: rgba(0, 204, 51, 0.05);
}

.pulse-dot {
  display: inline-block;
  width: 8px;
  height: 8px;
  background: #00ff41;
  border-radius: 50%;
  margin-right: 6px;
  box-shadow: 0 0 8px #00ff41;
  animation: pulse 1.5s infinite;
}

@keyframes pulse {
  0% { transform: scale(0.95); opacity: 0.7; }
  50% { transform: scale(1.2); opacity: 1; }
  100% { transform: scale(0.95); opacity: 0.7; }
}

.search-input {
  width: 100%;
  background: rgba(0, 15, 5, 0.9);
  border: 1px solid rgba(0, 204, 51, 0.3);
  color: #00ff41;
  padding: 10px 14px;
  border-radius: 6px;
  font-family: 'Fira Code', monospace;
  margin-bottom: 15px;
  outline: none;
}
.search-input:focus {
  border-color: #00ff41;
  box-shadow: 0 0 12px rgba(0, 255, 65, 0.3);
}

.interactive-box {
  background: rgba(0, 15, 4, 0.95);
  border: 1px solid rgba(0, 204, 51, 0.3);
  border-radius: 6px;
  padding: 18px;
  margin-bottom: 20px;
}
</style>

<!-- Mount Point for Interactive React App -->
<div id="daacs-root">
  <div style="text-align: center; padding: 40px; color: #00ff41;">
    <span class="pulse-dot"></span> Loading Interactive DAACS & Lessons Learned Dashboard...
  </div>
</div>

<!-- React 18 & Babel via CDN -->
<script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

<script type="text/babel">
const { useState } = React;

const unitData = [
  {
    id: 1,
    title: "Unit 1: Mindset & DAACS Assessment",
    assignment: "Introduction & Mindset Discussion + DAACS Assessment",
    summary: "Evaluated initial baseline in Self-Regulated Learning (SRL), metacognition, and academic mindset.",
    learned: "Identified my initial baseline scores in Self-Regulated Learning. While motivation was high, metacognition planning and help-seeking strategies were emerging. Realized college-level studying requires active self-monitoring.",
    movingForward: "Implemented structured self-evaluations after completing readings and assignments. Actively checking for comprehension rather than just completing tasks.",
    takeaways: ["Self-Regulated Learning is a core skill to cultivate.", "Metacognition monitoring prevents quiet knowledge gaps.", "Baseline assessments provide the roadmap for growth."],
    cyberLink: "In Cyber Operations, self-assessment is like running a vulnerability scan on your own skill set before deploying to real networks."
  },
  {
    id: 2,
    title: "Unit 2: Values, Goals, & Motivations",
    assignment: "Goals, Values, & Motivations Presentation",
    summary: "Defined core personal values (Integrity, Altruism, Honesty, Trust, Balance) and established SMART goals.",
    learned: "Explored how personal values influence academic commitment: Integrity, Honesty, Trust, Altruism, and Balance. Formulated SMART academic and career goals aimed at Red Teaming and Cyber Operations.",
    movingForward: "Using SMART goals as quarterly checkpoints. Selecting projects and CTF write-ups that directly align with Red Team Cyber Specialist career milestones.",
    takeaways: ["Integrity grounds professional ethics in tech.", "SMART goals convert vague wishes into actionable milestones.", "Values keep motivation high during intense sessions."],
    cyberLink: "Ethics and integrity are the cornerstone of offensive security and authorized penetration testing."
  },
  {
    id: 3,
    title: "Unit 3: Time Management & Big Rocks",
    assignment: "What are Your Big Rocks? Discussion + Organizing Your Schedule Assignment",
    summary: "Engineered an automated Google Apps Script Daily Goals Tracker to manage high-priority 'Big Rocks'.",
    learned: "Time management means working smarter, not harder. Identified 'Big Rocks' (Cyber Labs, Coursework, Technical Practice) and built an automated schedule parser with a 24h emoji routine and daily efficiency tracker.",
    movingForward: "Maintaining structured schedule tracking daily to eliminate friction, prevent last-minute stress, and maximize focus.",
    takeaways: ["Prioritize Big Rocks before filling hours with small pebbles.", "Automated tools and scripts remove friction from scheduling.", "Consistency builds momentum."],
    cyberLink: "Automating routine scheduling is identical to writing scripts to automate security scans."
  },
  {
    id: 4,
    title: "Unit 4: Engaging Your Success Network",
    assignment: "Engage with your Success Network Assignment",
    summary: "Initiated proactive communication with Academic Advisor, Success Coach, and Program Coordinators.",
    learned: "Reaching out for guidance is a strategic strength. Connected with my UMGC Success Network team to review my Academic Advising Report (AAR) and degree pathway.",
    movingForward: "Scheduling pre-registration check-ins with my Academic Advisor every term to stay ahead on Cyber Operations course prerequisites.",
    takeaways: ["Your Success Network is your strategic advisory team.", "Early planning prevents advising bottlenecks before registration.", "Advisors provide tailored degree mapping."],
    cyberLink: "Just like red teaming requires a coordinated team, navigating a degree benefits from a dedicated support network."
  },
  {
    id: 5,
    title: "Unit 5: Investigating Cyber Trends",
    assignment: "Preparing for Informational Interview Discussion + Investigating Career Trends Assignment",
    summary: "Researched cutting-edge trends in Cyber Operations, Red Teaming, and AI-driven security.",
    learned: "Investigated industry trends in offensive cyber: red team automation, cloud security assessments, STIG compliance, and AI-assisted threat detection. Prepared targeted interview questions for veteran cyber professionals.",
    movingForward: "Continuously updating my lab environment to include cloud security tools, containers, and automated vulnerability scanners.",
    takeaways: ["The cybersecurity landscape evolves daily.", "AI tools enhance vulnerability discovery when combined with human logic.", "Industry trends dictate what personal projects to build."],
    cyberLink: "Understanding blue team compliance tools makes you a significantly better red teamer."
  },
  {
    id: 6,
    title: "Unit 6: Informational Interview Insights",
    assignment: "Networking & Teamwork Discussion + Informational Interview Assignment",
    summary: "Interviewed a 22-year Tech Veteran with a Master's in Digital Forensics on breaking into cyber.",
    learned: "Gained valuable industry insights from a 22-year veteran in tech and digital forensics. Key takeaway: align personal projects directly with your target role and publish CTF write-ups publicly.",
    movingForward: "Actively publishing CTF write-ups (HackTheBox, TryHackMe, OverTheWire) directly on my public GitHub site to build a visible technical portfolio.",
    takeaways: ["Demonstrable proof of skill outweighs theoretical knowledge.", "Continuous hands-on labs build real-world problem-solving skills.", "Networking opens doors to hidden industry opportunities."],
    cyberLink: "Public write-ups serve as proof of work for offensive security roles."
  },
  {
    id: 7,
    title: "Unit 7: Identifying Support Services",
    assignment: "Support Services Summary Assignment",
    summary: "Evaluated 3 key UMGC resources: Writing Center, Tutoring Services, and Wellness Resources.",
    learned: "Detailed utility and realistic scenarios for the Writing Center (refining technical reports), Tutoring Services (tackling complex quantitative modules), and Wellness Resources (maintaining balance).",
    movingForward: "Submitting major writing drafts to the Writing Center prior to deadlines and utilizing stress management resources during peak weeks.",
    takeaways: ["Proactive resource utilization ensures top performance.", "Writing clarity is vital for technical penetration testing reports.", "Wellness maintenance prevents burn-out."],
    cyberLink: "Penetration testers spend significant time writing technical reports—the Writing Center sharpens this core skill."
  },
  {
    id: 8,
    title: "Unit 8: Lessons Learned & Future Growth",
    assignment: "Final Capstone Reflection & Portfolio Integration",
    summary: "Synthesized all 8 units into a unified strategic plan for completing my Cyber Operations degree.",
    learned: "Reflecting across all 8 units demonstrated transformation from establishing baseline SRL scores in Unit 1 to building automated schedules, engaging support networks, and building a public portfolio.",
    movingForward: "Maintaining this interactive DAACS & Notes repository throughout my entire degree program at UMGC as a living portfolio of technical growth.",
    takeaways: ["Reflection turns experience into actionable wisdom.", "Self-regulated learning is a lifelong professional habit.", "Finish strong and keep pushing boundaries."],
    cyberLink: "Continuous reflection and learning are mandatory to stay ahead in cyber security."
  }
];

const srlMetrics = [
  { name: "Metacognition Monitoring", initial: 45, current: 92 },
  { name: "Metacognition Planning", initial: 50, current: 95 },
  { name: "Time Management & Routines", initial: 40, current: 94 },
  { name: "Help-Seeking & Networking", initial: 35, current: 90 },
  { name: "Understanding & Deep Study", initial: 55, current: 91 },
  { name: "Self-Efficacy & Mindset", initial: 60, current: 96 }
];

const valuesList = [
  { name: "Integrity", desc: "Upholding strict ethical standards in penetration testing and offensive security." },
  { name: "Altruism", desc: "Sharing knowledge and helping peers troubleshoot complex technical labs." },
  { name: "Honesty", desc: "Accurately reporting vulnerabilities without exaggeration in security audits." },
  { name: "Trust", desc: "Building dependable relationships with team members and academic advisors." },
  { name: "Balance", desc: "Maintaining physical wellness, family time, and technical study focus." }
];

function DaacsApp() {
  const [activeTab, setActiveTab] = useState("all");
  const [searchQuery, setSearchQuery] = useState("");
  const [showRadar, setShowRadar] = useState(true);
  const [activeValue, setActiveValue] = useState(0);

  // Demo Schedule Tasks (Simulation Only)
  const [demoTasks, setDemoTasks] = useState([
    { id: 1, time: "07:00 - 08:30", title: "Morning Routine & System Diagnostic Check", category: "Routine", done: true },
    { id: 2, time: "09:00 - 12:00", title: "Cyber Operations Technical Module", category: "Academic", done: true },
    { id: 3, time: "12:30 - 14:00", title: "Red Team CTF Lab Practice (HackTheBox)", category: "Cyber Lab", done: true },
    { id: 4, time: "14:30 - 17:00", title: "PACE 111 Assignment & Reflection Writing", category: "Academic", done: true },
    { id: 5, time: "17:30 - 19:30", title: "Fitness & Wellness Rest Break", category: "Wellness", done: true },
    { id: 6, time: "20:00 - 22:00", title: "GitHub Notes & CTF Write-up Documentation", category: "Cyber Lab", done: false }
  ]);

  const toggleTask = (id) => {
    setDemoTasks(demoTasks.map(t => t.id === id ? { ...t, done: !t.done } : t));
  };

  const completedCount = demoTasks.filter(t => t.done).length;
  const efficiencyScore = Math.round((completedCount / demoTasks.length) * 100);

  const filteredUnits = unitData.filter(u => {
    if (activeTab !== "all" && u.id !== parseInt(activeTab)) return false;
    if (searchQuery.trim() === "") return true;
    const q = searchQuery.toLowerCase();
    return u.title.toLowerCase().includes(q) || 
           u.learned.toLowerCase().includes(q) || 
           u.movingForward.toLowerCase().includes(q) ||
           u.cyberLink.toLowerCase().includes(q);
  });

  return (
    <div class="daacs-container">
      {/* Header */}
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', flexWrap: 'wrap', borderBottom: '1px solid rgba(0,204,51,0.2)', paddingBottom: '12px', marginBottom: '15px' }}>
        <div>
          <h2 style={{ color: '#00ff41', margin: 0, fontSize: '1.15rem' }}>
            <span class="pulse-dot"></span> PACE 111 // DAACS & LESSONS LEARNED
          </h2>
          <span style={{ fontSize: '0.75rem', color: '#7abf7a' }}>
            Degree Path: Cyber Operations | Section: 2265
          </span>
        </div>
        <div style={{ textAlign: 'right', fontSize: '0.75rem', color: '#00cc33' }}>
          Interactive Capstone Portfolio | Session 2026
        </div>
      </div>

      {/* Search Input */}
      <input 
        type="text" 
        class="search-input" 
        placeholder="🔍 Search units, cyber topics, CTFs, tracker, writing center..." 
        value={searchQuery}
        onChange={(e) => setSearchQuery(e.target.value)}
      />

      {/* Navigation Bar */}
      <div style={{ marginBottom: '15px', display: 'flex', flexWrap: 'wrap', gap: '4px' }}>
        <button class={`daacs-nav-btn ${activeTab === 'all' ? 'active' : ''}`} onClick={() => setActiveTab('all')}>
          ⚡ All Units (1-8)
        </button>
        {[1,2,3,4,5,6,7,8].map(num => (
          <button key={num} class={`daacs-nav-btn ${activeTab === String(num) ? 'active' : ''}`} onClick={() => setActiveTab(String(num))}>
            Unit {num}
          </button>
        ))}
        <button class={`daacs-nav-btn ${activeTab === 'tracker' ? 'active' : ''}`} onClick={() => setActiveTab('tracker')}>
          📅 Daily Tracker (Demo)
        </button>
        <button class={`daacs-nav-btn ${activeTab === 'values' ? 'active' : ''}`} onClick={() => setActiveTab('values')}>
          💎 Values & SMART Goals
        </button>
      </div>

      {/* SRL Growth Radar Gauge */}
      <div style={{ background: 'rgba(0,18,5,0.9)', border: '1px solid rgba(0,204,51,0.25)', borderRadius: '6px', padding: '16px', marginBottom: '20px' }}>
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '10px' }}>
          <h3 style={{ color: '#00ff41', margin: 0, fontSize: '0.95rem' }}>
            📊 Self-Regulated Learning (SRL) Growth Gauge: Baseline vs Final Mastery
          </h3>
          <button onClick={() => setShowRadar(!showRadar)} class="daacs-nav-btn" style={{ fontSize: '0.7rem' }}>
            {showRadar ? "Hide Gauge" : "Show Gauge"}
          </button>
        </div>

        {showRadar && (
          <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(240px, 1fr))', gap: '12px' }}>
            {srlMetrics.map((m, idx) => (
              <div key={idx} style={{ background: 'rgba(0,10,3,0.6)', padding: '10px', borderRadius: '4px', border: '1px solid rgba(0,204,51,0.1)' }}>
                <div style={{ display: 'flex', justifyContent: 'space-between', fontSize: '0.75rem', marginBottom: '4px' }}>
                  <span style={{ color: '#c8ffc8' }}>{m.name}</span>
                  <span style={{ color: '#00ff41', fontWeight: 'bold' }}>{m.current}% <span style={{ fontSize: '0.65rem', color: '#7abf7a' }}>(+{(m.current - m.initial)}%)</span></span>
                </div>
                <div class="metric-bar-bg">
                  <div class="metric-bar-fill" style={{ width: `${m.current}%` }}></div>
                </div>
                <div style={{ fontSize: '0.65rem', color: 'rgba(0,204,51,0.5)', textAlign: 'right' }}>
                  Week 1 Baseline: {m.initial}%
                </div>
              </div>
            ))}
          </div>
        )}
      </div>

      {/* Demo Daily Tracker Tab */}
      {activeTab === 'tracker' && (
        <div class="interactive-box">
          <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '12px', flexWrap: 'wrap' }}>
            <div>
              <span class="unit-badge">INTERACTIVE DEMO</span>
              <h3 style={{ color: '#00ff41', margin: '4px 0 0 0', fontSize: '1rem' }}>
                📅 Unit 3 Highlight: Simulated Daily Goals Tracker
              </h3>
              <span style={{ fontSize: '0.72rem', color: '#7abf7a' }}>
                Interactive demonstration of Google Apps Script schedule parsing & time-block efficiency
              </span>
            </div>
            <div style={{ background: 'rgba(0,204,51,0.15)', border: '1px solid #00ff41', padding: '6px 14px', borderRadius: '6px', textAlign: 'center', marginTop: '6px' }}>
              <div style={{ fontSize: '0.65rem', color: '#7abf7a' }}>SIMULATED EFFICIENCY</div>
              <div style={{ fontSize: '1.25rem', color: '#00ff41', fontWeight: 'bold' }}>{efficiencyScore}%</div>
            </div>
          </div>

          <div style={{ marginBottom: '15px' }}>
            {demoTasks.map(t => (
              <div key={t.id} class="tracker-item" onClick={() => toggleTask(t.id)} style={{ cursor: 'pointer' }}>
                <div style={{ display: 'flex', alignItems: 'center', gap: '10px' }}>
                  <input type="checkbox" checked={t.done} onChange={() => {}} style={{ accentColor: '#00ff41' }} />
                  <span style={{ color: '#00ff41', fontSize: '0.75rem', width: '100px' }}>{t.time}</span>
                  <span style={{ color: t.done ? '#c8ffc8' : '#7abf7a', textDecoration: t.done ? 'none' : 'line-through' }}>{t.title}</span>
                </div>
                <span class="unit-badge" style={{ fontSize: '0.65rem' }}>{t.category}</span>
              </div>
            ))}
          </div>

          <div style={{ fontSize: '0.75rem', color: '#7abf7a', background: 'rgba(0,20,6,0.6)', padding: '10px', borderRadius: '4px' }}>
            💡 <em>Click checkboxes above to simulate dynamic score updates. Routine time-blocking prevents last-minute stress.</em>
          </div>
        </div>
      )}

      {/* Values & SMART Goals Tab */}
      {activeTab === 'values' && (
        <div class="interactive-box">
          <span class="unit-badge">UNIT 2 HIGHLIGHT</span>
          <h3 style={{ color: '#00ff41', margin: '4px 0 10px 0', fontSize: '1rem' }}>
            💎 Interactive Values & Ethics Compass
          </h3>
          <div style={{ display: 'flex', gap: '6px', flexWrap: 'wrap', marginBottom: '12px' }}>
            {valuesList.map((v, i) => (
              <button 
                key={i} 
                class={`daacs-nav-btn ${activeValue === i ? 'active' : ''}`}
                onClick={() => setActiveValue(i)}
              >
                {v.name}
              </button>
            ))}
          </div>
          <div style={{ background: 'rgba(0,10,3,0.8)', padding: '14px', borderRadius: '6px', border: '1px solid rgba(0,204,51,0.2)' }}>
            <div style={{ color: '#00ff41', fontWeight: 'bold', fontSize: '0.9rem' }}>
              Value Focus: {valuesList[activeValue].name}
            </div>
            <div style={{ fontSize: '0.82rem', color: '#c8ffc8', marginTop: '6px', lineHeight: '1.5' }}>
              {valuesList[activeValue].desc}
            </div>
          </div>
        </div>
      )}

      {/* Unit Cards List */}
      <div>
        {filteredUnits.length === 0 ? (
          <div style={{ textAlign: 'center', padding: '20px', color: '#7abf7a' }}>
            No units match your search query "{searchQuery}".
          </div>
        ) : (
          filteredUnits.map(unit => (
            <div key={unit.id} class="unit-card">
              <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'flex-start', flexWrap: 'wrap' }}>
                <div>
                  <span class="unit-badge">UNIT {unit.id}</span>
                  <h3 style={{ color: '#00ff41', margin: '4px 0 6px 0', fontSize: '1rem' }}>{unit.title}</h3>
                  <div style={{ fontSize: '0.75rem', color: '#7abf7a', marginBottom: '8px' }}>
                    <strong>Assignment:</strong> {unit.assignment}
                  </div>
                </div>
              </div>

              <div style={{ fontSize: '0.82rem', color: '#c8ffc8', lineHeight: '1.6', marginBottom: '10px' }}>
                {unit.summary}
              </div>

              <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(280px, 1fr))', gap: '10px', marginTop: '10px' }}>
                <div style={{ background: 'rgba(0,10,3,0.6)', padding: '10px', borderRadius: '4px', borderLeft: '3px solid #00cc33' }}>
                  <div style={{ color: '#00ff41', fontSize: '0.75rem', fontWeight: 'bold' }}>💡 What I Learned:</div>
                  <div style={{ fontSize: '0.76rem', color: '#c8ffc8', marginTop: '4px' }}>{unit.learned}</div>
                </div>

                <div style={{ background: 'rgba(0,10,3,0.6)', padding: '10px', borderRadius: '4px', borderLeft: '3px solid #00ff41' }}>
                  <div style={{ color: '#00ff41', fontSize: '0.75rem', fontWeight: 'bold' }}>🚀 How I Will Use It Moving Forward:</div>
                  <div style={{ fontSize: '0.76rem', color: '#c8ffc8', marginTop: '4px' }}>{unit.movingForward}</div>
                </div>
              </div>

              <div style={{ marginTop: '10px', background: 'rgba(0,30,10,0.4)', padding: '8px 12px', borderRadius: '4px', fontSize: '0.75rem', color: '#7abf7a' }}>
                🛡️ <strong>Cyber Operations Connection:</strong> {unit.cyberLink}
              </div>
            </div>
          ))
        )}
      </div>

      {/* AI Use Disclosure Box */}
      <div style={{ marginTop: '25px', paddingTop: '15px', borderTop: '1px dashed rgba(0,204,51,0.3)', textAlign: 'center', fontSize: '0.78rem', color: '#7abf7a' }}>
        <div style={{ color: '#00ff41', fontWeight: 'bold', marginBottom: '4px' }}>AI USE DISCLOSURE</div>
        <div>I did not use generative AI in the completion of this discussion.</div>
      </div>
    </div>
  );
}

const rootElement = document.getElementById('daacs-root');
if (rootElement) {
  const root = ReactDOM.createRoot(rootElement);
  root.render(<DaacsApp />);
}
</script>
