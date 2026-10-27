<script lang="ts">
  import { PageContainer, PageHeader, Card, Badge, Button } from '@cecepazhar/caui';

  let nodes = $state([
    { name: 'Hostinger VPS Gateway', ip: '100.76.150.46', services: 'Coolify, Traefik, PostgreSQL, Redis, n8n', status: 'Online', ram: '4.8 / 8 GB' },
    { name: 'YPC Dedicated Node', ip: '100.127.232.32', services: 'Dokploy, Gitea, Nextcloud, Imgproxy', status: 'Online', ram: '12.4 / 32 GB' },
    { name: 'Tencent Cloud Node', ip: '100.96.8.82', services: 'Content Hub, CAOrch, Traefik :80', status: 'Online', ram: '2.1 / 4 GB' },
    { name: 'ThinkPad X1 Workstation', ip: '100.78.73.124', services: 'Hermes Agent, 9Router, CAShell Local', status: 'Online', ram: '9.2 / 16 GB' }
  ]);
</script>

<PageContainer class="p-6 space-y-6 max-w-7xl mx-auto">
  <PageHeader title="Fleet & Infrastructure Nodes" subtitle="Tailscale mesh network, Dokploy runners, and hardware telemetry" accent="emerald">
    {#snippet action()}
      <div class="flex items-center gap-2">
        <Button variant="outline" size="sm">Probe Mesh</Button>
      </div>
    {/snippet}
  </PageHeader>

  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    {#each nodes as n}
      <Card class="p-5 space-y-3 shadow-2xs">
        <div class="flex items-start justify-between">
          <div>
            <h3 class="font-bold text-base text-neutral-900 dark:text-white">{n.name}</h3>
            <p class="font-mono text-xs text-sky-600 dark:text-sky-400 mt-0.5">{n.ip}</p>
          </div>
          <Badge variant="success" size="sm">{n.status}</Badge>
        </div>
        <p class="text-xs text-neutral-500">{n.services}</p>
        <div class="pt-2 border-t border-neutral-100 dark:border-neutral-800 flex justify-between text-xs text-neutral-400">
          <span>Memory Usage</span>
          <span class="font-mono font-medium text-neutral-300">{n.ram}</span>
        </div>
      </Card>
    {/each}
  </div>
</PageContainer>
