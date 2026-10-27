<script lang="ts">
  import { PageContainer, PageHeader, Card, Badge, Button } from '@cecepazhar/caui';

  let projects = $state([
    { name: 'Hotel Grand Sunshine', slug: 'grand-sunshine', client: 'PT Ratna Forever', status: 'Active', progress: 100, team: 'X1 Team', contract: 'Rp 12,000,000 / yr' },
    { name: 'Rollerskool.com RBS', slug: 'rollerskool-rbs', client: 'Coach Tom', status: 'Active', progress: 92, team: 'Bench Squad', contract: 'Rp 32,400,000 / yr' },
    { name: 'PBS Solopreneur', slug: 'pbs-solopreneur', client: 'Internal Product', status: 'Development', progress: 78, team: 'Prof. Cecep', contract: 'SaaS Suite' },
    { name: 'FathStore Solo Native', slug: 'fathstore-native', client: 'Fathforce Solo', status: 'Testing', progress: 95, team: 'Rust Squad', contract: 'Commercial Native' },
    { name: 'JurnalUmi Accounting', slug: 'jurnalumi-app', client: 'Internal Product', status: 'Maintenance', progress: 85, team: 'Bench Squad', contract: 'Cloud SaaS' },
    { name: 'SaptaDaya Platform', slug: 'saptadaya-com', client: 'PT Saptadaya', status: 'Completed', progress: 100, team: 'External', contract: 'Rp 15,000,000' }
  ]);
</script>

<PageContainer class="p-6 space-y-6 max-w-7xl mx-auto">
  <PageHeader title="Projects Management" subtitle="Client contracts, enterprise roadmaps, and autonomous delivery" accent="emerald">
    {#snippet action()}
      <div class="flex items-center gap-2">
        <Button variant="outline" size="sm">Filter Slices</Button>
        <Button variant="primary" size="sm">New Project</Button>
      </div>
    {/snippet}
  </PageHeader>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
    {#each projects as prj}
      <Card class="p-5 flex flex-col justify-between space-y-4 hover:border-emerald-500/50 transition-all shadow-2xs">
        <div>
          <div class="flex items-start justify-between gap-2">
            <div>
              <h3 class="font-bold text-base text-neutral-900 dark:text-white">{prj.name}</h3>
              <p class="text-xs text-neutral-500 dark:text-neutral-400 mt-0.5">{prj.client}</p>
            </div>
            {#if prj.status === 'Active'}
              <Badge variant="success" size="sm">{prj.status}</Badge>
            {:else if prj.status === 'Development' || prj.status === 'Testing'}
              <Badge variant="warning" size="sm">{prj.status}</Badge>
            {:else}
              <Badge variant="secondary" size="sm">{prj.status}</Badge>
            {/if}
          </div>

          <div class="mt-4 space-y-2">
            <div class="flex justify-between text-xs">
              <span class="text-neutral-500">Progress</span>
              <span class="font-semibold text-neutral-900 dark:text-white">{prj.progress}%</span>
            </div>
            <div class="w-full bg-neutral-200 dark:bg-neutral-800 h-1.5 rounded-full overflow-hidden">
              <div class="bg-emerald-500 h-full rounded-full" style="width: {prj.progress}%"></div>
            </div>
          </div>
        </div>

        <div class="pt-3 border-t border-neutral-100 dark:border-neutral-800/80 flex items-center justify-between text-xs">
          <span class="text-neutral-500 font-mono">{prj.contract}</span>
          <span class="text-emerald-600 dark:text-emerald-400 font-medium">{prj.team}</span>
        </div>
      </Card>
    {/each}
  </div>
</PageContainer>
