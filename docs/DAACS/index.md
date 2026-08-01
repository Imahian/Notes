# 🛡️ PACE 111 // DAACS & Lessons Learned
> **Student:** Ahian Diaz | **Course:** PACE 111: Program and Career Exploration | **Section:** 2265  
> **Instructor:** David Ferguson | **Degree Path:** Cyber Operations | **Date:** August 2026

---

<style>
/* ── Custom DAACS Component Styling ── */
.daacs-container {
  font-family: 'Fira Code', monospace;
  color: #c8ffc8;
  background: rgba(0, 12, 4, 0.75);
  border: 1px solid rgba(0, 204, 51, 0.3);
  border-radius: 8px;
  padding: 20px;
  margin-top: 15px;
  box-shadow: 0 0 25px rgba(0, 204, 51, 0.08);
}

.daacs-nav-btn {
  background: rgba(0, 40, 12, 0.7);
  color: #7abf7a;
  border: 1px solid rgba(0, 204, 51, 0.25);
  padding: 8px 14px;
  border-radius: 6px;
  cursor: pointer;
  font-family: 'Fira Code', monospace;
  font-size: 0.8rem;
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
  background: rgba(0, 20, 6, 0.85);
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
const { useState, useEffect } = React;

const unitData = [
  {
    id: 1,
    title: "Unit 1: Mindset & DAACS Assessment",
    assignment: "Introduction & Mindset Discussion + DAACS Assessment",
    summary: "Evaluated initial baseline in Self-Regulated Learning (SRL), metacognition, and academic mindset.",
    learned: "I discovered my initial baseline scores in Self-Regulated Learning. While my motivation was high, my metacognition planning and help-seeking strategies were in the emerging phase. I realized that academic success requires active monitoring rather than passive reading.",
    movingForward: "I am implementing structured self-evaluations after completing every reading and assignment. I actively check for comprehension rather than just checking off tasks.",
    takeaways: ["Self-Regulated Learning is a skill that can be built.", "Metacognition monitoring prevents quiet knowledge gaps.", "Baseline assessments provide the roadmap for growth."],
    cyberLink: "In Cyber Operations, self-assessment is like running a vulnerability scan on your own skill set before deploying to real networks."
  },
  {
    id: 2,
    title: "Unit 2: Values, Goals, & Motivations",
    assignment: "Goals, Values, & Motivations Presentation",
    summary: "Defined core personal values (Integrity, Altruism, Honesty, Trust, Balance) and established SMART goals.",
    learned: "Identified how my military background as an Army Aircraft Electrician influences my personal values: Integrity, Honesty, Trust, Altruism, and Balancing. Formulated SMART academic and career goals aimed at transitioning into Red Teaming and Cyber Operations.",
    movingForward: "I use my SMART goals as quarterly checkpoints. Every project I choose, including GitHub CTF write-ups, directly aligns with my goal of becoming a Red Team Cyber Specialist.",
    takeaways: ["Integrity and Altruism ground professional ethics in tech.", "SMART goals convert vague wishes into actionable milestones.", "Values keep motivation high during intense academic sessions."],
    cyberLink: "Ethics and integrity are the cornerstone of offensive security and authorized penetration testing."
  },
  {
    id: 3,
    title: "Unit 3: Time Management & Big Rocks",
    assignment: "What are Your Big Rocks? Discussion + Organizing Your Schedule Assignment",
    summary: "Analyzed time perception and engineered a custom automated Google Apps Script Daily Goals Tracker.",
    learned: "Time management means working smarter, not harder. I identified my 'Big Rocks' (Army duties, Cyber Labs, Family, PACE 111) and built a custom Google Sheets + Apps Script system with a 24h emoji routine, military-time range parser, and daily efficiency tracker.",
    movingForward: "I maintain my Daily Goals Tracker system every morning at 00:00. Syncing my schedule with Google Calendar ensures zero missed deadlines.",
    takeaways: ["Prioritize Big Rocks before filling hours with small pebbles.", "Automated tools and scripts remove friction from routine tracking.", "Consistency builds momentum."],
    cyberLink: "Automating routine scheduling is identical to writing bash/python scripts to automate security scans."
  },
  {
    id: 4,
    title: "Unit 4: Engaging Your Success Network",
    assignment: "Engage with your Success Network Assignment",
    summary: "Planned and initiated active communication with Success Coach, Academic Advisor, and MEC.",
    learned: "Reaching out for guidance is a strategic strength, not a sign of weakness. I connected with my UMGC Success Network partners (Success Coach & Military Education Coordinator) to review my Academic Advising Report (AAR) and degree pathway.",
    movingForward: "I schedule pre-registration check-ins with my Academic Advisor every term to stay ahead on Cyber Operations course prerequisites.",
    takeaways: ["Your Success Network is your strategic command team.", "Early planning prevents advising bottlenecks before registration.", "Advisors provide tailored degree mapping for military students."],
    cyberLink: "Just like red teaming requires a coordinated team, navigating a degree benefits from a dedicated support network."
  },
  {
    id: 5,
    title: "Unit 5: Investigating Cyber Trends",
    assignment: "Preparing for Informational Interview Discussion + Investigating Career Trends Assignment",
    summary: "Researched cutting-edge trends in Cyber Operations, Red Teaming, and AI-driven vulnerability management.",
    learned: "Investigated key industry trends in offensive cyber: red team automation, cloud security assessments, STIG compliance, and AI-assisted threat detection. Prepared targeted interview questions for veteran cyber professionals.",
    movingForward: "I continuously update my lab environment to include cloud security tools, containers, and automated vulnerability scanners like ACAS/Nessus.",
    takeaways: ["The cybersecurity landscape evolves daily.", "AI tools enhance vulnerability discovery when combined with human logic.", "Industry trends dictate what personal projects to build."],
    cyberLink: "Understanding blue team tools (STIGs, eMASS) makes you a significantly better red teamer."
  },
  {
    id: 6,
    title: "Unit 6: Informational Interview Insights",
    assignment: "Networking & Teamwork Discussion + Informational Interview Assignment",
    summary: "Interviewed Terrance Perry (Retired Navy Vet, Master's Digital Forensics) on breaking into cyber.",
    learned: "Sat down with Terrance Perry, a 22-year Navy veteran and Digital Forensics Master. Key takeaway: align personal projects directly with your target role. He advised building red team labs and publishing CTF write-ups on GitHub so hiring managers can verify skills.",
    movingForward: "I am actively publishing CTF write-ups (HackTheBox, TryHackMe, OverTheWire) directly on my GitHub Notes site (`imahian.github.io/Notes`).",
    takeaways: ["Demonstrable proof of skill outweighs theoretical knowledge.", "Military transition to cyber is achievable with focused hands-on labs.", "Networking opens doors to hidden industry opportunities."],
    cyberLink: "Public write-ups serve as proof of work for offensive security roles."
  },
  {
    id: 7,
    title: "Unit 7: Identifying Support Services",
    assignment: "Support Services Summary Assignment",
    summary: "Evaluated 3 key UMGC resources: Writing Center, Tutoring Services, and Wellness Resources.",
    learned: "Detailed personal utility and specific scenarios for the Writing Center (refining APA technical reports), Tutoring Services (tackling advanced quantitative modules), and Wellness Resources (managing work-life-military balance).",
    movingForward: "I submit major writing drafts to the Writing Center 5 days prior to deadlines and utilize stress management tools during peak operational weeks.",
    takeaways: ["Proactive resource utilization ensures top academic performance.", "Writing clarity is vital for technical penetration testing reports.", "Wellness maintenance prevents burn-out."],
    cyberLink: "Penetration testers spend 50% of their time writing technical reports—the Writing Center sharpens this core skill."
  },
  {
    id: 8,
    title: "Unit 8: Lessons Learned & Future Growth",
    assignment: "Final Capstone Reflection & Portfolio Integration",
    summary: "Synthesized all 8 units into a unified strategic plan for completing my Cyber Operations degree.",
    learned: "Reflecting across all 8 units demonstrated my transformation from a new student uncertain of academic routines into a disciplined, self-regulated learner with automated tracking, an active professional network, and clear career milestones.",
    movingForward: "I will maintain this interactive DAACS & Notes repository throughout my entire degree program at UMGC as a living portfolio of my technical growth.",
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

function DaacsApp() {
  const [activeTab, setActiveTab] = useState("all");
  const [searchQuery, setSearchQuery] = useState("");
  const [selectedUnit, setSelectedUnit] = useState(null);
  const [showRadar, setShowRadar] = useState(true);

  // Daily Tracker Interactive State
  const [trackerTasks, setTrackerTasks] = useState([
    { id: 1, time: "06:00 - 08:00", title: "Army Morning Brief & Flight Line Check", category: "Military", done: true },
    { id: 2, time: "08:00 - 12:00", title: "Avionics Electrical Maintenance", category: "Military", done: true },
    { id: 3, time: "12:00 - 13:30", title: "Cyber Red Team CTF Lab (HackTheBox)", category: "Cyber Lab", done: true },
    { id: 4, time: "14:00 - 17:00", title: "UMGC PACE 111 Module & Writing", category: "Academic", done: true },
    { id: 5, time: "17:00 - 19:00", title: "Fitness & Family Time", category: "Wellness", done: true },
    { id: 6, time: "19:00 - 21:30", title: "Scripting & GitHub Notes Documentation", category: "Cyber Lab", done: false }
  ]);

  const toggleTask = (id) => {
    setTrackerTasks(trackerTasks.map(t => t.id === id ? { ...t, done: !t.done } : t));
  };

  const completedCount = trackerTasks.filter(t => t.done).length;
  const efficiencyScore = Math.round((completedCount / trackerTasks.length) * 100);

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
      {/* Title Header */}
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', flexWrap: 'wrap', borderBottom: '1px solid rgba(0,204,51,0.2)', paddingBottom: '12px', marginBottom: '15px' }}>
        <div>
          <h2 style={{ color: '#00ff41', margin: 0, fontSize: '1.2rem' }}>
            <span class="pulse-dot"></span> AHIAN DIAZ // PACE 111 DAACS REFLECTION
          </h2>
          <span style={{ fontSize: '0.75rem', color: '#7abf7a' }}>
            Cyber Operations Major | Army Aircraft Electrician | Section 2265
          </span>
        </div>
        <div style={{ textAlign: 'right', fontSize: '0.75rem', color: '#00cc33' }}>
          Instructor: David Ferguson | Final Session 2026
        </div>
      </div>

      {/* Search & Navigation Bar */}
      <input 
        type="text" 
        class="search-input" 
        placeholder="🔍 Search units, cyber topics, STIGs, Terrance, tracker, writing center..." 
        value={searchQuery}
        onChange={(e) => setSearchQuery(e.target.value)}
      />

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
          📅 Daily Tracker Simulator
        </button>
        <button class={`daacs-nav-btn ${activeTab === 'network' ? 'active' : ''}`} onClick={() => setActiveTab('network')}>
          🎙️ Informational Interview
        </button>
      </div>

      {/* SRL Growth Radar / Metrics Section */}
      <div style={{ background: 'rgba(0,18,5,0.9)', border: '1px solid rgba(0,204,51,0.25)', borderRadius: '6px', padding: '16px', marginBottom: '20px' }}>
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '10px' }}>
          <h3 style={{ color: '#00ff41', margin: 0, fontSize: '0.95rem' }}>
            📊 Self-Regulated Learning (SRL) Competency Matrix: Week 1 vs Week 8
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
                  Initial Baseline: {m.initial}%
                </div>
              </div>
            ))}
          </div>
        )}
      </div>

      {/* Daily Tracker Simulator Tab */}
      {activeTab === 'tracker' && (
        <div style={{ background: 'rgba(0,15,4,0.95)', border: '1px solid rgba(0,204,51,0.3)', borderRadius: '6px', padding: '18px', marginBottom: '20px' }}>
          <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '12px' }}>
            <div>
              <h3 style={{ color: '#00ff41', margin: 0, fontSize: '1rem' }}>
                📅 Unit 3 Highlight: Google Apps Script Daily Tracker Simulator
              </h3>
              <span style={{ fontSize: '0.72rem', color: '#7abf7a' }}>
                Based on Ahian's DailyGoalsTracker.gs system with 24h emoji routine & calendar sync
              </span>
            </div>
            <div style={{ background: 'rgba(0,204,51,0.15)', border: '1px solid #00ff41', padding: '6px 12px', borderRadius: '6px', textAlign: 'center' }}>
              <div style={{ fontSize: '0.65rem', color: '#7abf7a' }}>DAILY EFFICIENCY</div>
              <div style={{ fontSize: '1.2rem', color: '#00ff41', fontWeight: 'bold' }}>{efficiencyScore}%</div>
            </div>
          </div>

          <div style={{ marginBottom: '15px' }}>
            {trackerTasks.map(t => (
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

          <div style={{ fontSize: '0.75rem', color: '#7abf7a', fontStyle: 'italic', background: 'rgba(0,20,6,0.6)', padding: '10px', borderRadius: '4px' }}>
            💡 <strong>System Architecture:</strong> Reads weekly routine table from Google Sheets, groups consecutive emoji blocks into military-time ranges, and updates daily efficiency metrics dynamically.
          </div>
        </div>
      )}

      {/* Informational Interview Tab */}
      {activeTab === 'network' && (
        <div style={{ background: 'rgba(0,15,4,0.95)', border: '1px solid rgba(0,204,51,0.3)', borderRadius: '6px', padding: '18px', marginBottom: '20px' }}>
          <h3 style={{ color: '#00ff41', margin: '0 0 10px 0', fontSize: '1rem' }}>
            🎙️ Unit 6 Highlight: Informational Interview with Terrance Perry
          </h3>
          <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(280px, 1fr))', gap: '12px' }}>
            <div style={{ background: 'rgba(0,10,3,0.8)', padding: '14px', borderRadius: '6px', border: '1px solid rgba(0,204,51,0.2)' }}>
              <div style={{ color: '#00ff41', fontWeight: 'bold', fontSize: '0.85rem' }}>👨‍💻 Interviewee Profile</div>
              <div style={{ fontSize: '0.78rem', color: '#c8ffc8', marginTop: '6px' }}>
                <strong>Terrance Perry</strong> — Retired Navy Veteran (22 Years Service), Master's in Digital Forensics.
              </div>
              <div style={{ fontSize: '0.72rem', color: '#7abf7a', marginTop: '4px' }}>
                Current Role: Blue Team / Vulnerability Management Lead (ACAS, Nessus, STIGs, eMASS).
              </div>
            </div>

            <div style={{ background: 'rgba(0,10,3,0.8)', padding: '14px', borderRadius: '6px', border: '1px solid rgba(0,204,51,0.2)' }}>
              <div style={{ color: '#00ff41', fontWeight: 'bold', fontSize: '0.85rem' }}>🔑 Golden Advice for Ahian</div>
              <div style={{ fontSize: '0.78rem', color: '#c8ffc8', marginTop: '6px' }}>
                "Align your personal projects with the exact career path you want. Build Red Team CTF labs and publish write-ups on GitHub so employers can see your proof of work."
              </div>
              <div style={{ fontSize: '0.72rem', color: '#00ff41', marginTop: '6px' }}>
                ➔ Direct Result: Host CTF writeups on <code>imahian.github.io/Notes</code>
              </div>
            </div>
          </div>
        </div>
      )}

      {/* Unit Cards List */}
      <div>
        {filteredUnits.length === 0 ? (
          <div style={{ textAlignment: 'center', padding: '20px', color: '#7abf7a' }}>
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

---

## 📜 Full Written Essay & Unit Reflections (Rubric Documentation)

### 📌 Unit 1: Introduction & Mindset Discussion & DAACS Assessment
- **What I Learned:** Taking the DAACS assessment during Unit 1 revealed my baseline in Self-Regulated Learning (SRL). While my motivation was in the mastering range, my metacognitive planning and help-seeking strategies were still emerging. I learned that college-level studying requires active self-monitoring rather than simply skimming text.
- **How I Will Use It Moving Forward:** I actively monitor my comprehension during readings by pausing to summarize key concepts. In Cyber Operations, self-assessment is essential when diagnosing complex network anomalies or conducting security audits.
- **Key Takeaways:** Baseline testing highlights growth areas; metacognition transforms passive reading into active learning.

### 📌 Unit 2: Goals, Values, & Motivations
- **What I Learned:** Exploring my core personal values—Integrity, Altruism, Honesty, Trust, and Balance—clarified why I am pursuing my degree in Cyber Operations. As an active-duty Army Aircraft Electrician, integrity and trust are non-negotiable.
- **How I Will Use It Moving Forward:** I set SMART academic goals that directly link to my long-term career aspirations in Red Teaming and penetration testing. Every course I complete serves as a step toward mastering security operations.
- **Key Takeaways:** Personal values ground academic commitment; SMART goals turn long-term dreams into structured weekly steps.

### 📌 Unit 3: What are Your Big Rocks? & Organizing Your Schedule
- **What I Learned:** Effective time management is about working smarter, not harder. I identified my "Big Rocks"—Army flight line duties, Cyber CTF labs, family commitments, and PACE 111 assignments. To manage these, I engineered an automated **Daily Goals Tracker** using Google Apps Script that parses my weekly 24-hour emoji routine into daily time-block ranges and syncs directly with Google Calendar.
- **How I Will Use It Moving Forward:** I use this automated tracker daily to maintain operational discipline and track efficiency metrics across my remaining degree courses.
- **Key Takeaways:** Prioritize high-impact "Big Rocks" first; automation removes friction from personal scheduling.

### 📌 Unit 4: Engage with your Success Network
- **What I Learned:** Navigating a degree does not have to be a solo effort. Reaching out to my Success Network—including my Academic Advisor and Military Education Coordinator (MEC)—provided critical clarity on my Academic Advising Report (AAR) and course sequence.
- **How I Will Use It Moving Forward:** I schedule regular check-ins before registration periods to ensure I satisfy all prerequisites for advanced Cyber Operations modules.
- **Key Takeaways:** Support networks amplify student success; asking for advice early prevents degree bottlenecks.

### 📌 Unit 5: Preparing for Informational Interview & Investigating Trends
- **What I Learned:** Researching cybersecurity trends showed the high demand for professionals skilled in red team operations, automated vulnerability management (ACAS/Nessus), and STIG compliance. I prepared structured interview questions targeting practical day-to-day security workflows.
- **How I Will Use It Moving Forward:** I align my hands-on practice labs with current industry standards, ensuring I build skills in vulnerability scanning and cloud security.
- **Key Takeaways:** Industry research keeps learning relevant; understanding blue team compliance makes you a stronger red teamer.

### 📌 Unit 6: Networking & Teamwork & Informational Interview
- **What I Learned:** I interviewed **Terrance Perry**, a retired Navy veteran with 22 years of service and a Master's in Digital Forensics. Terrance emphasized that employers look for verifiable proof of work. His main advice: point personal projects at your target career path and publish CTF write-ups publicly.
- **How I Will Use It Moving Forward:** I publish my CTF lab write-ups (HackTheBox, TryHackMe, OverTheWire) directly on my public GitHub site (`imahian.github.io/Notes`), building a visible technical portfolio.
- **Key Takeaways:** Public proof-of-work validates technical skill; military experience translates effectively into cybersecurity roles.

### 📌 Unit 7: Support Services Summary
- **What I Learned:** Explored three vital UMGC resources: the **Writing Center** (complimentary draft reviews), **Tutoring Services** (no-cost quantitative assistance), and **Wellness Resources** (mental health & stress management).
- **How I Will Use It Moving Forward:** I submit major writing assignments to the Writing Center to ensure technical reports are clear and properly formatted in APA style, and I leverage wellness resources to maintain balance during demanding operational cycles.
- **Key Takeaways:** Writing precision is critical for security reporting; proactive self-care sustains long-term academic productivity.

### 📌 Unit 8: Reflecting on Lessons Learned & Looking Ahead
- **What I Learned:** Tying together all eight units demonstrated how far I have come—from establishing baseline SRL scores in Unit 1 to building an automated daily schedule, engaging my support network, interviewing industry veterans, and creating a public technical portfolio.
- **How I Will Use It Moving Forward:** I will maintain this interactive DAACS & Notes portal as a central hub for all my future UMGC cybersecurity coursework and technical write-ups.
- **Key Takeaways:** Reflection turns experience into lasting wisdom; consistency and structured planning guarantee degree completion.

---

> **AI Use Disclosure:**  
> I did not use generative AI in the completion of this discussion.
