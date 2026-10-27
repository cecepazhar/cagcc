<script lang="ts">
  import { PageContainer, PageHeader, Card, Badge, Button } from '@cecepazhar/caui';

  let clients = $state([
    { name: 'Hotel Grand Sunshine', company: 'PT Ratna Forever', phone: '+62811-2195-294', invoices: 8, status: 'Active', tier: 'Enterprise' },
    { name: 'Rollerskool.com', company: 'Rollerskool Academy', phone: 'finance@rollerskool.com', invoices: 4, status: 'Active', tier: 'Partner' },
    { name: 'Justus Steakhouse', company: 'Justus Group', phone: '-', invoices: 1, status: 'Active', tier: 'Corporate' },
    { name: 'PGRI Kota Bandung', company: 'PGRI', phone: '-', invoices: 2, status: 'Active', tier: 'Organization' },
    { name: 'Kopontren ALIF', company: 'ALIF Foundation', phone: '-', invoices: 1, status: 'Active', tier: 'Corporate' }
  ]);
</script>

<PageContainer class="p-6 space-y-6 max-w-7xl mx-auto">
  <PageHeader title="Client Directory" subtitle="Corporate partners, invoicing profiles, and account contacts" accent="emerald">
    {#snippet action()}
      <div class="flex items-center gap-2">
        <Button variant="primary" size="sm">Add Client</Button>
      </div>
    {/snippet}
  </PageHeader>

  <Card class="p-0 overflow-hidden shadow-2xs">
    <div class="overflow-x-auto">
      <table class="w-full text-sm text-left">
        <thead class="bg-neutral-50 dark:bg-neutral-900/60 text-xs text-neutral-500 uppercase border-b border-neutral-200 dark:border-neutral-800">
          <tr>
            <th class="px-6 py-3 font-semibold">Client Name</th>
            <th class="px-6 py-3 font-semibold">Company</th>
            <th class="px-6 py-3 font-semibold">Contact</th>
            <th class="px-6 py-3 font-semibold">Tier</th>
            <th class="px-6 py-3 font-semibold">Status</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-neutral-100 dark:divide-neutral-800/50">
          {#each clients as c}
            <tr class="hover:bg-neutral-50 dark:hover:bg-neutral-800/40 transition-colors">
              <td class="px-6 py-4 font-semibold text-neutral-900 dark:text-white">{c.name}</td>
              <td class="px-6 py-4 text-neutral-600 dark:text-neutral-300">{c.company}</td>
              <td class="px-6 py-4 text-xs font-mono text-neutral-400">{c.phone}</td>
              <td class="px-6 py-4"><Badge variant="outline" size="sm">{c.tier}</Badge></td>
              <td class="px-6 py-4"><Badge variant="success" size="sm">{c.status}</Badge></td>
            </tr>
          {/each}
        </tbody>
      </table>
    </div>
  </Card>
</PageContainer>
