<script lang="ts">
  import { PageContainer, PageHeader, Card, Badge, Button } from '@cecepazhar/caui';

  let websites = $state([
    { domain: 'fathforce.com', role: 'Ecosystem Master', node: 'Hostinger VPS', ssl: 'Let\'s Encrypt / CF', status: 'Online', latency: '42ms' },
    { domain: 'gcc.fathforce.com', role: 'GCC Command Core', node: 'Hostinger VPS', ssl: 'Cloudflare Edge', status: 'Online', latency: '35ms' },
    { domain: 'cecepazhar.com', role: 'Founder Portal', node: 'Hostinger VPS', ssl: 'Cloudflare Edge', status: 'Online', latency: '48ms' },
    { domain: 'caterm.fathforce.com', role: 'CATerm Landing', node: 'Hostinger VPS', ssl: 'Let\'s Encrypt', status: 'Online', latency: '38ms' },
    { domain: 'camark.fathforce.com', role: 'CAMark Studio', node: 'Hostinger VPS', ssl: 'Cloudflare Edge', status: 'Online', latency: '40ms' },
    { domain: 'caui.fathforce.com', role: 'Design System', node: 'YPC Dokploy', ssl: 'Traefik SSL', status: 'Online', latency: '65ms' },
    { domain: 'rbs.rollerskool.com', role: 'RBS Skate Academy', node: 'Hostinger VPS', ssl: 'Cloudflare Edge', status: 'Online', latency: '52ms' },
    { domain: 'lampeganmotorbdg.com', role: 'Lampegan Motor CMS', node: 'Hostinger VPS', ssl: 'Let\'s Encrypt', status: 'Online', latency: '75ms' }
  ]);
</script>

<PageContainer class="p-6 space-y-6 max-w-7xl mx-auto">
  <PageHeader title="Websites & Domains" subtitle="Multi-mirror edge status, Cloudflare proxy, and production portals" accent="emerald">
    {#snippet action()}
      <div class="flex items-center gap-2">
        <Button variant="outline" size="sm" onclick={() => window.location.reload()}>Ping All Endpoints</Button>
        <Button variant="primary" size="sm">Add Domain</Button>
      </div>
    {/snippet}
  </PageHeader>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
    <Card class="p-4 shadow-2xs">
      <div class="text-xs text-neutral-500 uppercase font-semibold">Active Portals</div>
      <div class="text-2xl font-bold text-neutral-900 dark:text-white mt-1">8 Domains</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs text-neutral-500 uppercase font-semibold">Average Latency</div>
      <div class="text-2xl font-bold text-emerald-600 dark:text-emerald-400 mt-1">45 ms</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs text-neutral-500 uppercase font-semibold">SSL Status</div>
      <div class="text-2xl font-bold text-emerald-600 dark:text-emerald-400 mt-1">100% Valid</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs text-neutral-500 uppercase font-semibold">DNS Provider</div>
      <div class="text-2xl font-bold text-sky-600 dark:text-sky-400 mt-1">Cloudflare Edge</div>
    </Card>
  </div>

  <Card class="p-0 overflow-hidden shadow-2xs">
    <div class="px-6 py-4 border-b border-neutral-200 dark:border-neutral-800">
      <h2 class="text-base font-bold text-neutral-900 dark:text-white">Domain Health Matrix</h2>
    </div>
    <div class="overflow-x-auto">
      <table class="w-full text-sm text-left">
        <thead class="bg-neutral-50 dark:bg-neutral-900/60 text-xs text-neutral-500 uppercase border-b border-neutral-200 dark:border-neutral-800">
          <tr>
            <th class="px-6 py-3 font-semibold">Domain</th>
            <th class="px-6 py-3 font-semibold">Role</th>
            <th class="px-6 py-3 font-semibold">Host Node</th>
            <th class="px-6 py-3 font-semibold">SSL Cert</th>
            <th class="px-6 py-3 font-semibold">Latency</th>
            <th class="px-6 py-3 font-semibold">Status</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-neutral-100 dark:divide-neutral-800/50">
          {#each websites as site}
            <tr class="hover:bg-neutral-50 dark:hover:bg-neutral-800/40 transition-colors">
              <td class="px-6 py-4 font-mono font-semibold text-xs text-sky-600 dark:text-sky-400">
                <a href="https://{site.domain}" target="_blank" class="hover:underline flex items-center gap-1.5">
                  {site.domain}
                  <svg class="w-3 h-3 text-neutral-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg>
                </a>
              </td>
              <td class="px-6 py-4 font-medium text-neutral-900 dark:text-white">{site.role}</td>
              <td class="px-6 py-4 text-xs text-neutral-500">{site.node}</td>
              <td class="px-6 py-4 text-xs font-mono text-neutral-400">{site.ssl}</td>
              <td class="px-6 py-4 text-xs font-mono text-emerald-500">{site.latency}</td>
              <td class="px-6 py-4">
                <Badge variant="success" size="sm">{site.status}</Badge>
              </td>
            </tr>
          {/each}
        </tbody>
      </table>
    </div>
  </Card>
</PageContainer>
