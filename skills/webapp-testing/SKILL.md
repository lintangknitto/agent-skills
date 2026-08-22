---
name: webapp-testing
description: Toolkit untuk menguji aplikasi web lokal dengan Playwright — verifikasi fungsionalitas frontend, debugging perilaku UI, capture screenshot browser, dan cek log browser. Pakai saat perlu memastikan fitur web berjalan di browser nyata, bukan saat unit test murni atau test API saja.
license: MIT
compatibility: "Membutuhkan Playwright MCP (npx @playwright/mcp) dan browser yang terinstal"
metadata:
  category: frontend & testing
  author: lintangknitto
  version: "1.0.0"
  source: anthropics/claude-code (webapp-testing, MIT) — diadaptasi untuk format superset
allowed-tools: []
disallowed-tools: []
argument-hint: "<url atau path aplikasi>"
when_to_use: "Saat user minta verifikasi UI, debugging tampilan, atau testing E2E di browser lokal"
disable-model-invocation: false
user-invocable: true
model: inherit
effort: medium
compatible_with: [claude-code, opencode, antigravity, commandcode]
---

# Webapp Testing

Toolkit untuk menguji aplikasi web lokal memakai Playwright MCP. Cocok untuk memverifikasi fitur frontend end-to-end di browser nyata, bukan sekadar unit test.

## Kapan dipakai

- User minta "cek apakah fitur X jalan di browser", "test login flow", "verifikasi tampilan"
- Debugging UI yang tidak bisa direproduksi dari log saja
- Butuh bukti visual (screenshot) atau evidence browser (console, network)
- Pasangan alami untuk `test-driven-development` (TDD untuk unit) dan `systematic-debugging` (saat test gagal)

## Kapan TIDAK dipakai

- Test unit/integration murni tanpa browser (pakai `test-driven-development` atau `react-testing`)
- Test API/backend tanpa UI
- Validasi statis/linting (pakai `code-review-and-quality`)

## Langkah-langkah

1. **Pastikan Playwright MCP aktif** — cek `mcp.playwright` di `opencode.json` (`npx -y @playwright/mcp@latest`). Jika belum, instal dulu.
2. **Jalankan aplikasi lokal** — `npm run dev`, `pnpm dev`, atau command sesuai project, catat URL (mis. `http://localhost:3000`).
3. **Navigasi & interaksi** — pakai tool Playwright: `playwright_browser_navigate`, `playwright_browser_click`, `playwright_browser_type`, `playwright_browser_snapshot` untuk verifikasi DOM.
4. **Kumpulkan evidence** — `playwright_browser_console_messages`, `playwright_browser_network_requests`, `playwright_browser_take_screenshot`. Simpan artifact jika perlu.
5. **Verifikasi & iterasi** — bandingkan hasil dengan ekspektasi; jika gagal, hand-off ke `systematic-debugging` (fase Root Cause Investigation) atau tulis failing test via `test-driven-development`.

## Referensi

- `references/playwright-mcp.md` — daftar tool Playwright MCP dan contoh pemakaian (on-demand)
- `references/e2e-pattern.md` — pola Page Object Model dari skill `e2e-testing`
- Terkait: `e2e-testing` (Playwright E2E patterns), `react-testing` (component test), `test-driven-development` (RED-GREEN-REFACTOR)
