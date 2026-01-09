/* =========================
   TBD Funding Site — app.js
   - Dropdown menu
   - Mobile drawer
   - Reveal on scroll
   - Funding Fit selector (home)
   - Stepper (home)
   - Proof filters (home)
   - Accordion cards (home)
   - Footer year
   ========================= */

(function () {
  const $ = (sel, root = document) => root.querySelector(sel);
  const $$ = (sel, root = document) => Array.from(root.querySelectorAll(sel));

  // Footer year
  const yearEl = $('[data-year]');
  if (yearEl) yearEl.textContent = String(new Date().getFullYear());

  // Elevate header on scroll
  const header = $('[data-elevate-on-scroll]');
  const onScroll = () => {
    if (!header) return;
    header.classList.toggle('is-elevated', window.scrollY > 8);
  };
  onScroll();
  window.addEventListener('scroll', onScroll, { passive: true });

  // Dropdown menu
  const trigger = $('[data-menu-trigger]');
  const menu = $('[data-menu]');
  const closeMenu = () => {
    if (!trigger || !menu) return;
    trigger.setAttribute('aria-expanded', 'false');
    menu.classList.remove('is-open');
  };
  const openMenu = () => {
    if (!trigger || !menu) return;
    trigger.setAttribute('aria-expanded', 'true');
    menu.classList.add('is-open');
  };
  if (trigger && menu) {
    trigger.addEventListener('click', (e) => {
      e.stopPropagation();
      const isOpen = menu.classList.contains('is-open');
      isOpen ? closeMenu() : openMenu();
    });
    document.addEventListener('click', closeMenu);
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') closeMenu();
    });
  }

  // Mobile drawer
  const burger = $('[data-burger]');
  const drawer = $('[data-drawer]');
  const openDrawer = () => {
    if (!drawer || !burger) return;
    drawer.classList.add('is-open');
    drawer.setAttribute('aria-hidden', 'false');
    burger.setAttribute('aria-expanded', 'true');
    document.documentElement.style.overflow = 'hidden';
  };
  const closeDrawer = () => {
    if (!drawer || !burger) return;
    drawer.classList.remove('is-open');
    drawer.setAttribute('aria-hidden', 'true');
    burger.setAttribute('aria-expanded', 'false');
    document.documentElement.style.overflow = '';
  };

  if (burger && drawer) {
    burger.addEventListener('click', (e) => {
      e.preventDefault();
      const isOpen = drawer.classList.contains('is-open');
      isOpen ? closeDrawer() : openDrawer();
    });
    $$('[data-drawer-close]', drawer).forEach((el) => el.addEventListener('click', closeDrawer));
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') closeDrawer();
    });
  }

  // Reveal on scroll
  const reveals = $$('.reveal');
  if (reveals.length) {
    const io = new IntersectionObserver(
      (entries) => {
        entries.forEach((ent) => {
          if (ent.isIntersecting) {
            ent.target.classList.add('is-in');
            io.unobserve(ent.target);
          }
        });
      },
      { threshold: 0.15 }
    );
    reveals.forEach((el) => io.observe(el));
  }

  // Accordion cards (Home options preview)
  $$('[data-acc]').forEach((btn) => {
    btn.addEventListener('click', () => {
      btn.classList.toggle('is-open');
    });
  });

  // Funding Fit selector (Home)
  const fitRoot = $('[data-fit]');
  if (fitRoot) {
    const chips = $$('[data-fit-chip]', fitRoot);
    const out = $('[data-fit-output]', fitRoot);

    const payload = {
      inventory: [
        { k: 'Likely lane', v: 'Working Capital / Line' },
        { k: 'Typical timeline', v: 'Fast (days)' },
        { k: 'What we’ll need', v: 'Statements + basics' },
      ],
      growth: [
        { k: 'Likely lane', v: 'Line / Term / RBF' },
        { k: 'Typical timeline', v: 'Fast → Moderate' },
        { k: 'What we’ll need', v: 'Revenue consistency' },
      ],
      bridge: [
        { k: 'Likely lane', v: 'Bridge / Working Capital' },
        { k: 'Typical timeline', v: 'Fast (days)' },
        { k: 'What we’ll need', v: 'Statements + plan' },
      ],
    };

    const render = (key) => {
      if (!out) return;
      const cards = payload[key] || payload.inventory;
      out.innerHTML = cards
        .map(
          (c) => `
            <div class="fitcard">
              <div class="fitcard__k">${escapeHtml(c.k)}</div>
              <div class="fitcard__v">${escapeHtml(c.v)}</div>
            </div>
          `
        )
        .join('');
    };

    const setActive = (btn) => {
      chips.forEach((b) => {
        const on = b === btn;
        b.classList.toggle('is-active', on);
        b.setAttribute('aria-selected', on ? 'true' : 'false');
      });
      render(btn.getAttribute('data-fit-key') || 'inventory');
    };

    chips.forEach((btn) => btn.addEventListener('click', () => setActive(btn)));
    render('inventory');
  }

  // Stepper (Home)
  const stepper = $('[data-stepper]');
  if (stepper) {
    const tabs = $$('[data-step]', stepper);
    const panel = $('[data-stepper-panel]', stepper);

    const steps = {
      1: {
        title: 'Apply (2–3 min)',
        you: 'Basic business details.',
        we: 'Quick fit + route to the right lane.',
        time: 'Same day review (typical).',
      },
      2: {
        title: 'We package your file',
        you: 'Connect statements / upload docs.',
        we: 'Prep it to win underwriting.',
        time: 'Fast if docs are ready.',
      },
      3: {
        title: 'Offers, not guesswork',
        you: 'Pick the lane you prefer.',
        we: 'Explain tradeoffs in plain English.',
        time: 'You’ll see choices, not one door.',
      },
      4: {
        title: 'Funded',
        you: 'Sign + confirm.',
        we: 'Keep you moving through close.',
        time: 'Funding timing depends on lane.',
      },
    };

    const renderStep = (n) => {
      const s = steps[n] || steps[1];
      if (!panel) return;
      panel.innerHTML = `
        <div class="h3" style="font-weight:900; letter-spacing:-.02em; margin-bottom:10px;">${escapeHtml(s.title)}</div>
        <div class="twocol">
          <div>
            <div class="k">You do</div>
            <div class="v">${escapeHtml(s.you)}</div>
          </div>
          <div>
            <div class="k">We do</div>
            <div class="v">${escapeHtml(s.we)}</div>
          </div>
        </div>
        <div class="badge">⟡ Typical: ${escapeHtml(s.time)}</div>
      `;
    };

    const setTab = (btn) => {
      tabs.forEach((t) => {
        const on = t === btn;
        t.classList.toggle('is-active', on);
        t.setAttribute('aria-selected', on ? 'true' : 'false');
      });
      renderStep(btn.getAttribute('data-step'));
    };

    tabs.forEach((btn) => btn.addEventListener('click', () => setTab(btn)));
    renderStep(1);
  }

  // Proof filters (Home)
  const filterRoot = $('[data-filters]');
  const grid = $('[data-proof-grid]');
  if (filterRoot && grid) {
    const buttons = $$('[data-filter]', filterRoot);
    const cards = $$('[data-tags]', grid);

    const apply = (tag) => {
      cards.forEach((c) => {
        const tags = (c.getAttribute('data-tags') || '').split(/\s+/).filter(Boolean);
        const show = tag === 'all' ? true : tags.includes(tag);
        c.classList.toggle('is-hidden', !show);
      });
    };

    const setBtn = (btn) => {
      buttons.forEach((b) => b.classList.toggle('is-active', b === btn));
      apply(btn.getAttribute('data-filter') || 'all');
    };

    buttons.forEach((btn) => btn.addEventListener('click', () => setBtn(btn)));
    apply('all');
  }

  // Helpers
  function escapeHtml(str) {
    return String(str)
      .replaceAll('&', '&amp;')
      .replaceAll('<', '&lt;')
      .replaceAll('>', '&gt;')
      .replaceAll('"', '&quot;')
      .replaceAll("'", '&#039;');
  }
})();
