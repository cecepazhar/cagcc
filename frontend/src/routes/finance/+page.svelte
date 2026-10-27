<script lang="ts">
  import { PageContainer, PageHeader, Card, Badge, Button, Table } from '@cecepazhar/caui';
  import { onMount } from 'svelte';
  import { invoke } from '@tauri-apps/api/core';

  let isLoading = $state(true);
  let totalRevenue = $state('Rp 0');
  let outstanding = $state('Rp 0');
  let paidInvoices = $state(0);
  let unpaidInvoices = $state(0);

  let payments = $state([
    { invoice: 'INV-202610-0009', client: 'Hotel Grand Sunshine', amount: 'Rp 1,110,000', status: 'Unpaid', date: '26 Okt 2026' },
    { invoice: 'INV-202610-0008', client: 'Rollerskool.com', amount: 'Rp 2,700,000', status: 'Sent', date: '21 Okt 2026' },
    { invoice: 'INV-202610-0007', client: 'Rollerskool.com', amount: 'Rp 2,700,000', status: 'Paid', date: '21 Okt 2026' },
    { invoice: 'INV-202610-0006', client: 'Hotel Grand Sunshine', amount: 'Rp 1,110,000', status: 'Paid', date: '05 Okt 2026' },
    { invoice: 'INV-202610-0005', client: 'Hotel Grand Sunshine', amount: 'Rp 1,110,000', status: 'Paid', date: '05 Okt 2026' }
  ]);

  onMount(async () => {
    try {
      const apiToken = localStorage.getItem('cagcc_api_token') || 'gcc_pro_token';
      // In real implementation, fetch from https://gcc.fathforce.com/api/v1/finance
      setTimeout(() => {
        totalRevenue = 'Rp 22,400,000';
        outstanding = 'Rp 2,700,000';
        paidInvoices = 8;
        unpaidInvoices = 2;
        isLoading = false;
      }, 600);
    } catch (e) {
      isLoading = false;
    }
  });
</script>

<PageContainer class="p-6 space-y-6 max-w-7xl mx-auto">
  <PageHeader title="Finance & Invoices" subtitle="Receivables, invoices, payment history, and revenue sync" accent="emerald">
    {#snippet action()}
      <div class="flex items-center gap-2">
        <Button variant="outline" size="sm" onclick={() => window.location.reload()}>Refresh Data</Button>
        <Button variant="primary" size="sm">Create New Invoice</Button>
      </div>
    {/snippet}
  </PageHeader>

  <!-- KPI Metrics -->
  <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
    <Card class="p-4 shadow-2xs">
      <div class="text-xs font-medium text-neutral-500 dark:text-neutral-400 uppercase tracking-wider">Total Revenue</div>
      <div class="text-2xl font-bold text-neutral-900 dark:text-white mt-1">{totalRevenue}</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs font-medium text-neutral-500 dark:text-neutral-400 uppercase tracking-wider">Outstanding</div>
      <div class="text-2xl font-bold text-rose-600 dark:text-rose-400 mt-1">{outstanding}</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs font-medium text-neutral-500 dark:text-neutral-400 uppercase tracking-wider">Paid Invoices</div>
      <div class="text-2xl font-bold text-emerald-600 dark:text-emerald-400 mt-1">{paidInvoices}</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs font-medium text-neutral-500 dark:text-neutral-400 uppercase tracking-wider">Unpaid Invoices</div>
      <div class="text-2xl font-bold text-amber-600 dark:text-amber-400 mt-1">{unpaidInvoices}</div>
    </Card>
  </div>

  <!-- Invoices Table -->
  <Card class="p-0 overflow-hidden shadow-2xs">
    <div class="px-6 py-4 border-b border-neutral-200 dark:border-neutral-800 flex items-center justify-between">
      <h2 class="text-base font-bold text-neutral-900 dark:text-white">Recent Transactions</h2>
      <Badge variant="secondary" size="sm">Live GCC Sync</Badge>
    </div>
    <div class="overflow-x-auto">
      <table class="w-full text-sm">
        <thead>
          <tr class="border-b border-neutral-200 dark:border-neutral-800 text-neutral-500 dark:text-neutral-400 text-left bg-neutral-50 dark:bg-neutral-900/50">
            <th class="px-6 py-3 font-semibold uppercase text-xs">Invoice</th>
            <th class="px-6 py-3 font-semibold uppercase text-xs">Client</th>
            <th class="px-6 py-3 font-semibold uppercase text-xs text-right">Amount</th>
            <th class="px-6 py-3 font-semibold uppercase text-xs">Status</th>
            <th class="px-6 py-3 font-semibold uppercase text-xs">Date</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-neutral-100 dark:divide-neutral-800/50">
          {#each payments as p}
            <tr class="hover:bg-neutral-50 dark:hover:bg-neutral-800/40 transition-colors">
              <td class="px-6 py-4 font-mono text-xs font-semibold text-sky-600 dark:text-sky-400">{p.invoice}</td>
              <td class="px-6 py-4 font-medium text-neutral-900 dark:text-white">{p.client}</td>
              <td class="px-6 py-4 text-right font-mono text-xs">{p.amount}</td>
              <td class="px-6 py-4">
                {#if p.status === 'Paid'}
                  <Badge variant="success" size="sm">{p.status}</Badge>
                {:else if p.status === 'Unpaid'}
                  <Badge variant="danger" size="sm">{p.status}</Badge>
                {:else}
                  <Badge variant="warning" size="sm">{p.status}</Badge>
                {/if}
              </td>
              <td class="px-6 py-4 text-xs text-neutral-500 dark:text-neutral-400">{p.date}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    </div>
  </Card>
</PageContainer>
