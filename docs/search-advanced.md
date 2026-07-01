# Advanced Search

<div id="adv-search-root">

<div class="adv-search-wrap">
  <div class="adv-search-bar">
    <span class="adv-search-icon">&#9654;</span>
    <input id="adv-input" type="text" placeholder="Search writeups, tools, CVEs..." autocomplete="off" spellcheck="false" />
    <span id="adv-clear" class="adv-clear" title="Clear">&#x2715;</span>
  </div>
  <ul id="adv-suggestions" class="adv-suggestions"></ul>
</div>

<div class="adv-filters">
  <div class="adv-filter-group">
    <span class="adv-filter-label">Platform</span>
    <button class="adv-chip active" data-filter="platform" data-value="">All</button>
    <button class="adv-chip" data-filter="platform" data-value="htb">HTB</button>
    <button class="adv-chip" data-filter="platform" data-value="otw">OTW</button>
    <button class="adv-chip" data-filter="platform" data-value="thm">THM</button>
    <button class="adv-chip" data-filter="platform" data-value="vulnhub">VulnHub</button>
    <button class="adv-chip" data-filter="platform" data-value="cve">CVE</button>
  </div>
  <div class="adv-filter-group">
    <span class="adv-filter-label">Difficulty</span>
    <button class="adv-chip active" data-filter="difficulty" data-value="">All</button>
    <button class="adv-chip diff-easy" data-filter="difficulty" data-value="easy">Easy</button>
    <button class="adv-chip diff-medium" data-filter="difficulty" data-value="medium">Medium</button>
    <button class="adv-chip diff-hard" data-filter="difficulty" data-value="hard">Hard</button>
    <button class="adv-chip diff-insane" data-filter="difficulty" data-value="insane">Insane</button>
  </div>
  <div class="adv-filter-group">
    <span class="adv-filter-label">Type</span>
    <button class="adv-chip active" data-filter="type" data-value="">All</button>
    <button class="adv-chip" data-filter="type" data-value="ctf">CTF</button>
    <button class="adv-chip" data-filter="type" data-value="cert">Cert</button>
    <button class="adv-chip" data-filter="type" data-value="tool">Tool</button>
  </div>
  <div class="adv-filter-group">
    <span class="adv-filter-label">Technique</span>
    <button class="adv-chip active" data-filter="tech" data-value="">All</button>
    <button class="adv-chip" data-filter="tech" data-value="web">Web</button>
    <button class="adv-chip" data-filter="tech" data-value="privesc">PrivEsc</button>
    <button class="adv-chip" data-filter="tech" data-value="ssh">SSH</button>
    <button class="adv-chip" data-filter="tech" data-value="sql">SQLi</button>
    <button class="adv-chip" data-filter="tech" data-value="xss">XSS</button>
    <button class="adv-chip" data-filter="tech" data-value="rce">RCE</button>
    <button class="adv-chip" data-filter="tech" data-value="lfi">LFI</button>
    <button class="adv-chip" data-filter="tech" data-value="brute">Brute Force</button>
  </div>
</div>

<div id="adv-stats" class="adv-stats"></div>
<div id="adv-results" class="adv-results"></div>

</div>

<style>
#adv-search-root { font-family: 'Fira Code', monospace; }

.adv-search-wrap { position: relative; margin-bottom: 1rem; }

.adv-search-bar {
  display: flex;
  align-items: center;
  background: rgba(0,12,4,0.88);
  border: 1px solid rgba(0,204,51,0.35);
  border-radius: 6px;
  padding: 0 14px;
  transition: border-color .2s, box-shadow .2s;
}
.adv-search-bar:focus-within {
  border-color: #00cc33;
  box-shadow: 0 0 16px rgba(0,204,51,0.2);
}

.adv-search-icon { color: rgba(0,204,51,0.5); font-size: 0.75rem; margin-right: 10px; }

#adv-input {
  flex: 1;
  background: transparent;
  border: none;
  outline: none;
  color: #c8ffc8;
  font-family: 'Fira Code', monospace;
  font-size: 1rem;
  padding: 14px 0;
  caret-color: #00ff41;
}
#adv-input::placeholder { color: rgba(0,204,51,0.3); }

.adv-clear {
  color: rgba(0,204,51,0.3);
  cursor: pointer;
  font-size: 0.85rem;
  padding: 4px;
  display: none;
  transition: color .2s;
}
.adv-clear:hover { color: #00ff41; }
.adv-clear.visible { display: block; }

.adv-suggestions {
  position: absolute;
  top: 100%;
  left: 0; right: 0;
  background: rgba(2,13,4,0.97);
  border: 1px solid rgba(0,204,51,0.25);
  border-top: none;
  border-radius: 0 0 6px 6px;
  list-style: none;
  margin: 0; padding: 0;
  z-index: 99;
  max-height: 260px;
  overflow-y: auto;
  display: none;
  backdrop-filter: blur(20px);
}
.adv-suggestions.open { display: block; }

.adv-suggestions li {
  padding: 10px 16px;
  cursor: pointer;
  color: #7abf7a;
  font-size: 0.82rem;
  border-bottom: 1px solid rgba(0,204,51,0.06);
  display: flex;
  align-items: center;
  gap: 10px;
}
.adv-suggestions li:hover,
.adv-suggestions li.selected {
  background: rgba(0,204,51,0.1);
  color: #00ff41;
}
.adv-suggestions li .sug-icon { color: rgba(0,204,51,0.4); font-size: 0.7rem; }
.adv-suggestions li .sug-title { flex: 1; }
.adv-suggestions li .sug-path { color: rgba(0,204,51,0.3); font-size: 0.7rem; }

.adv-filters {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-bottom: 1.2rem;
}

.adv-filter-group {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 6px;
}

.adv-filter-label {
  color: rgba(0,204,51,0.45);
  font-size: 0.68rem;
  text-transform: uppercase;
  letter-spacing: .1em;
  margin-right: 4px;
}

.adv-chip {
  background: rgba(0,12,4,0.7);
  border: 1px solid rgba(0,204,51,0.2);
  color: rgba(0,204,51,0.55);
  font-family: 'Fira Code', monospace;
  font-size: 0.72rem;
  padding: 4px 10px;
  border-radius: 4px;
  cursor: pointer;
  transition: all .18s;
}
.adv-chip:hover { border-color: rgba(0,204,51,0.5); color: #00cc33; }
.adv-chip.active {
  background: rgba(0,204,51,0.15);
  border-color: #00cc33;
  color: #00ff41;
  box-shadow: 0 0 8px rgba(0,204,51,0.2);
}
.diff-easy.active   { border-color: #00cc33; color: #00ff41; }
.diff-medium.active { border-color: #ffaa00; color: #ffaa00; box-shadow: 0 0 8px rgba(255,170,0,0.2); }
.diff-hard.active   { border-color: #ff4444; color: #ff4444; box-shadow: 0 0 8px rgba(255,68,68,0.2); }
.diff-insane.active { border-color: #cc00ff; color: #cc00ff; box-shadow: 0 0 8px rgba(204,0,255,0.2); }

.adv-stats {
  color: rgba(0,204,51,0.4);
  font-size: 0.72rem;
  margin-bottom: .8rem;
  min-height: 1.2em;
}

.adv-results { display: flex; flex-direction: column; gap: 10px; }

.adv-card {
  background: rgba(2,13,4,0.6);
  border: 1px solid rgba(0,204,51,0.12);
  border-radius: 6px;
  padding: 14px 18px;
  transition: border-color .18s, box-shadow .18s;
  cursor: pointer;
  text-decoration: none;
  display: block;
  color: inherit;
  backdrop-filter: blur(10px);
}
.adv-card:hover {
  border-color: rgba(0,204,51,0.4);
  box-shadow: 0 0 14px rgba(0,204,51,0.1);
  text-decoration: none;
  color: inherit;
}

.adv-card-title {
  color: #00ff41;
  font-size: 0.95rem;
  font-weight: 600;
  margin-bottom: 4px;
}
.adv-card-title mark {
  background: rgba(0,204,51,0.25);
  color: #00ff41;
  border-radius: 2px;
  padding: 0 2px;
}

.adv-card-path {
  color: rgba(0,204,51,0.35);
  font-size: 0.68rem;
  margin-bottom: 8px;
}

.adv-card-excerpt {
  color: #7abf7a;
  font-size: 0.78rem;
  line-height: 1.5;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
.adv-card-excerpt mark {
  background: rgba(0,204,51,0.18);
  color: #c8ffc8;
  border-radius: 2px;
  padding: 0 2px;
}

.adv-card-tags { display: flex; flex-wrap: wrap; gap: 5px; margin-top: 8px; }
.adv-tag {
  font-size: 0.65rem;
  padding: 2px 7px;
  border-radius: 3px;
  background: rgba(0,204,51,0.1);
  border: 1px solid rgba(0,204,51,0.25);
  color: #00cc33;
}
.adv-tag.diff-easy   { border-color: rgba(0,204,51,0.4); }
.adv-tag.diff-medium { background: rgba(255,170,0,0.08); border-color: rgba(255,170,0,0.3); color: #ffaa00; }
.adv-tag.diff-hard   { background: rgba(255,68,68,0.08); border-color: rgba(255,68,68,0.3); color: #ff6666; }
.adv-tag.diff-insane { background: rgba(204,0,255,0.08); border-color: rgba(204,0,255,0.3); color: #cc88ff; }

.adv-empty {
  text-align: center;
  color: rgba(0,204,51,0.3);
  padding: 3rem 0;
  font-size: 0.85rem;
}
</style>

<script>
(function() {
  const BASE = document.querySelector('base')
    ? document.querySelector('base').href
    : (location.pathname.replace(/\/[^/]*$/, '/'));

  const SITE_ROOT = (() => {
    const m = location.pathname.match(/^(\/[^/]+\/)/);
    return m ? m[1] : '/';
  })();

  const input       = document.getElementById('adv-input');
  const clearBtn    = document.getElementById('adv-clear');
  const sugList     = document.getElementById('adv-suggestions');
  const results     = document.getElementById('adv-results');
  const statsEl     = document.getElementById('adv-stats');

  let INDEX = [];
  let filters = { platform: '', difficulty: '', type: '', tech: '' };
  let sugIdx  = -1;
  let debTimer;

  // ── Load search index ──────────────────────────────────────────────────────
  fetch(SITE_ROOT + 'search/search_index.json')
    .then(r => r.json())
    .then(data => {
      INDEX = (data.docs || []).filter(d => d.title && d.location !== '.');
      statsEl.textContent = INDEX.length + ' documents indexed';
      render('', filters);
    })
    .catch(() => {
      statsEl.textContent = 'Search index not available in local preview — deploy to see results.';
    });

  // ── Helpers ────────────────────────────────────────────────────────────────
  function normLoc(loc) { return loc.toLowerCase(); }

  function inferPlatform(doc) {
    const l = normLoc(doc.location);
    if (l.includes('ctfs/htb') || l.includes('ctfs\\htb')) return 'htb';
    if (l.includes('ctfs/otw') || l.includes('ctfs\\otw')) return 'otw';
    if (l.includes('ctfs/thm') || l.includes('ctfs\\thm')) return 'thm';
    if (l.includes('ctfs/vhb') || l.includes('ctfs\\vhb')) return 'vulnhub';
    if (l.includes('cves/'))   return 'cve';
    return '';
  }

  function inferType(doc) {
    const l = normLoc(doc.location);
    if (l.startsWith('ctfs/') || l.startsWith('ctfs\\')) return 'ctf';
    if (l.startsWith('certs/') || l.startsWith('certs\\')) return 'cert';
    if (l.startsWith('tools/') || l.startsWith('tools\\')) return 'tool';
    if (l.startsWith('cves/') || l.startsWith('cves\\')) return 'cve';
    return '';
  }

  function getDocTags(doc) {
    return (doc.tags || []).map(t => t.toLowerCase());
  }

  function inferDifficulty(doc) {
    const tags = getDocTags(doc);
    for (const d of ['easy','medium','hard','insane']) {
      if (tags.includes(d)) return d;
    }
    const text = (doc.title + ' ' + (doc.text || '')).toLowerCase();
    for (const d of ['insane','hard','medium','easy']) {
      if (text.includes(d)) return d;
    }
    return '';
  }

  function matchesTech(doc, tech) {
    if (!tech) return true;
    const tags = getDocTags(doc);
    if (tags.includes(tech)) return true;
    const text = (doc.title + ' ' + (doc.text || '') + ' ' + doc.location).toLowerCase();
    const map = {
      web: ['web','http','https','html','php','flask'],
      privesc: ['privesc','privilege','sudo','suid','root'],
      ssh: ['ssh','openssh'],
      sql: ['sql','mysql','sqli','injection'],
      xss: ['xss','cross-site'],
      rce: ['rce','remote code','command injection','exec'],
      lfi: ['lfi','local file','path traversal'],
      brute: ['brute','hydra','rockyou','wordlist','crack']
    };
    return (map[tech] || [tech]).some(kw => text.includes(kw));
  }

  function scoreAndMatch(doc, query) {
    if (!query) return { match: true, score: 0, titleHL: doc.title, excerptHL: '' };
    const q  = query.toLowerCase();
    const t  = (doc.title || '').toLowerCase();
    const tx = (doc.text  || '').toLowerCase();

    const inTitle = t.includes(q);
    const inText  = tx.includes(q);
    if (!inTitle && !inText) return { match: false };

    const score = inTitle ? (t.startsWith(q) ? 3 : 2) : 1;

    function hl(str, q) {
      const re = new RegExp('(' + q.replace(/[.*+?^${}()|[\]\\]/g,'\\$&') + ')', 'gi');
      return str.replace(re, '<mark>$1</mark>');
    }

    let excerpt = '';
    if (inText) {
      const idx = tx.indexOf(q);
      const start = Math.max(0, idx - 60);
      const end   = Math.min(doc.text.length, idx + q.length + 140);
      excerpt = (start > 0 ? '…' : '') + doc.text.slice(start, end) + (end < doc.text.length ? '…' : '');
    }

    return {
      match: true,
      score,
      titleHL:   hl(doc.title, query),
      excerptHL: excerpt ? hl(excerpt, query) : ''
    };
  }

  function render(query, flt) {
    const q = query.trim();
    let docs = INDEX;

    // apply filters
    docs = docs.filter(d => {
      const plat = inferPlatform(d);
      const type = inferType(d);
      const diff = inferDifficulty(d);
      if (flt.platform  && plat !== flt.platform)  return false;
      if (flt.difficulty && diff !== flt.difficulty) return false;
      if (flt.type      && type !== flt.type && plat !== flt.type) return false;
      if (flt.tech      && !matchesTech(d, flt.tech)) return false;
      return true;
    });

    // apply query
    let scored = docs.map(d => ({ doc: d, ...scoreAndMatch(d, q) }))
                     .filter(x => x.match)
                     .sort((a,b) => b.score - a.score);

    statsEl.textContent = scored.length
      ? scored.length + ' result' + (scored.length > 1 ? 's' : '') + (q ? ' for "' + q + '"' : '')
      : '';

    if (!scored.length) {
      results.innerHTML = '<div class="adv-empty">No results' + (q ? ' for "' + q + '"' : '') + '</div>';
      return;
    }

    results.innerHTML = scored.slice(0, 40).map(({ doc, titleHL, excerptHL }) => {
      const tags    = getDocTags(doc);
      const inferred = [inferPlatform(doc), inferDifficulty(doc), inferType(doc)].filter(Boolean);
      const allTags = [...new Set([...inferred, ...tags])].filter(Boolean);
      const diff    = inferDifficulty(doc);

      const tagHtml = allTags.map(t => {
        const cls = t === 'easy' ? 'diff-easy'
                  : t === 'medium' ? 'diff-medium'
                  : t === 'hard'   ? 'diff-hard'
                  : t === 'insane' ? 'diff-insane' : '';
        return `<span class="adv-tag ${cls}">${t}</span>`;
      }).join('');

      const href = SITE_ROOT + doc.location;

      return `<a class="adv-card" href="${href}">
        <div class="adv-card-title">${titleHL}</div>
        <div class="adv-card-path">${doc.location}</div>
        ${excerptHL ? `<div class="adv-card-excerpt">${excerptHL}</div>` : ''}
        ${tagHtml ? `<div class="adv-card-tags">${tagHtml}</div>` : ''}
      </a>`;
    }).join('');
  }

  // ── Autocomplete suggestions ───────────────────────────────────────────────
  function buildSuggestions(q) {
    if (!q || q.length < 2) { hideSug(); return; }
    const lq = q.toLowerCase();
    const seen = new Set();
    const hits = [];
    for (const doc of INDEX) {
      if (hits.length >= 8) break;
      const t = (doc.title || '').toLowerCase();
      if (!t.includes(lq)) continue;
      if (seen.has(doc.title)) continue;
      seen.add(doc.title);
      hits.push(doc);
    }
    if (!hits.length) { hideSug(); return; }

    sugIdx = -1;
    sugList.innerHTML = hits.map((doc, i) => {
      const icon = inferType(doc) === 'ctf'  ? '⚑'
                 : inferType(doc) === 'cert' ? '✦'
                 : inferType(doc) === 'tool' ? '⚙'
                 : '◈';
      const path = doc.location.split('/').slice(0,3).join('/');
      return `<li data-idx="${i}" data-title="${doc.title}" data-loc="${doc.location}">
        <span class="sug-icon">${icon}</span>
        <span class="sug-title">${doc.title}</span>
        <span class="sug-path">${path}</span>
      </li>`;
    }).join('');

    sugList.classList.add('open');

    sugList.querySelectorAll('li').forEach(li => {
      li.addEventListener('mousedown', e => {
        e.preventDefault();
        input.value = li.dataset.title;
        hideSug();
        clearBtn.classList.add('visible');
        render(li.dataset.title, filters);
      });
    });
  }

  function hideSug() { sugList.classList.remove('open'); sugList.innerHTML = ''; sugIdx = -1; }

  // ── Events ─────────────────────────────────────────────────────────────────
  input.addEventListener('input', () => {
    const q = input.value;
    clearBtn.classList.toggle('visible', q.length > 0);
    clearTimeout(debTimer);
    debTimer = setTimeout(() => {
      buildSuggestions(q);
      render(q, filters);
    }, 80);
  });

  input.addEventListener('keydown', e => {
    const items = sugList.querySelectorAll('li');
    if (!items.length) return;
    if (e.key === 'ArrowDown') {
      e.preventDefault();
      sugIdx = Math.min(sugIdx + 1, items.length - 1);
      items.forEach((li,i) => li.classList.toggle('selected', i === sugIdx));
    } else if (e.key === 'ArrowUp') {
      e.preventDefault();
      sugIdx = Math.max(sugIdx - 1, -1);
      items.forEach((li,i) => li.classList.toggle('selected', i === sugIdx));
    } else if (e.key === 'Enter' && sugIdx >= 0) {
      e.preventDefault();
      const li = items[sugIdx];
      input.value = li.dataset.title;
      hideSug();
      clearBtn.classList.add('visible');
      render(li.dataset.title, filters);
    } else if (e.key === 'Escape') {
      hideSug();
    } else if (e.key === 'Tab' && sugIdx === -1 && items.length) {
      e.preventDefault();
      input.value = items[0].dataset.title;
      hideSug();
      render(input.value, filters);
    }
  });

  document.addEventListener('click', e => {
    if (!e.target.closest('#adv-search-root .adv-search-wrap')) hideSug();
  });

  clearBtn.addEventListener('click', () => {
    input.value = '';
    clearBtn.classList.remove('visible');
    hideSug();
    render('', filters);
    input.focus();
  });

  // ── Filter chips ───────────────────────────────────────────────────────────
  document.querySelectorAll('.adv-chip').forEach(chip => {
    chip.addEventListener('click', () => {
      const group = chip.dataset.filter;
      document.querySelectorAll(`.adv-chip[data-filter="${group}"]`)
              .forEach(c => c.classList.remove('active'));
      chip.classList.add('active');
      filters[group] = chip.dataset.value;
      render(input.value, filters);
    });
  });

})();
</script>
