<script lang="ts">
  import { PageContainer, PageHeader, Card, Badge, Button } from '@cecepazhar/caui';

  let articles = $state([
    { title: 'Solopreneur Hyper-Productive Framework', site: 'cecepazhar.com', lang: 'Bilingual (ID/EN)', status: 'Published', views: '1,420', date: '24 Okt 2026' },
    { title: 'Zero-Knowledge Architecture in Desktop Native', site: 'docs.fathforce.com', lang: 'EN', status: 'Published', views: '890', date: '21 Okt 2026' },
    { title: 'CAMark v1.0.25 Release Notes', site: 'camark.fathforce.com', lang: 'Bilingual (ID/EN)', status: 'Published', views: '2,150', date: '19 Okt 2026' },
    { title: 'CATerm SSH SFTP Terminal Deep Dive', site: 'caterm.fathforce.com', lang: 'EN', status: 'Published', views: '3,410', date: '16 Okt 2026' },
    { title: 'PostgreSQL vs SQLite STRICT in Offline-First POS', site: 'fathstore.com', lang: 'ID', status: 'Draft', views: '-', date: '14 Okt 2026' }
  ]);
</script>

<PageContainer class="p-6 space-y-6 max-w-7xl mx-auto">
  <PageHeader title="Content & Knowledge Base" subtitle="Bilingual portal articles, technical documentation, and ecosystem publishing" accent="emerald">
    {#snippet action()}
      <div class="flex items-center gap-2">
        <Button variant="outline" size="sm">Sync PostgreSQL</Button>
        <Button variant="primary" size="sm">New Article</Button>
      </div>
    {/snippet}
  </PageHeader>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
    <Card class="p-4 shadow-2xs">
      <div class="text-xs text-neutral-500 uppercase font-semibold">Total Articles</div>
      <div class="text-2xl font-bold text-neutral-900 dark:text-white mt-1">74 Articles</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs text-neutral-500 uppercase font-semibold">Bilingual Status</div>
      <div class="text-2xl font-bold text-emerald-600 dark:text-emerald-400 mt-1">EN + ID Live</div>
    </Card>
    <Card class="p-4 shadow-2xs">
      <div class="text-xs text-neutral-500 uppercase font-semibold">Postgres Storage</div>
      <div class="text-2xl font-bold text-sky-600 dark:text-sky-400 mt-1">site_pages table</div>
    </Card>
  </div>

  <Card class="p-0 overflow-hidden shadow-2xs">
    <div class="px-6 py-4 border-b border-neutral-200 dark:border-neutral-800">
      <h2 class="text-base font-bold text-neutral-900 dark:text-white">Published Content Overview</h2>
    </div>
    <div class="overflow-x-auto">
      <table class="w-full text-sm text-left">
        <thead class="bg-neutral-50 dark:bg-neutral-900/60 text-xs text-neutral-500 uppercase border-b border-neutral-200 dark:border-neutral-800">
          <tr>
            <th class="px-6 py-3 font-semibold">Title</th>
            <th class="px-6 py-3 font-semibold">Portal Site</th>
            <th class="px-6 py-3 font-semibold">Language</th>
            <th class="px-6 py-3 font-semibold">Views</th>
            <th class="px-6 py-3 font-semibold">Status</th>
            <th class="px-6 py-3 font-semibold">Date</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-neutral-100 dark:divide-neutral-800/50">
          {#each articles as a}
            <tr class="hover:bg-neutral-50 dark:hover:bg-neutral-800/40 transition-colors">
              <td class="px-6 py-4 font-semibold text-neutral-900 dark:text-white">{a.title}</td>
              <td class="px-6 py-4 font-mono text-xs text-sky-600 dark:text-sky-400">{a.site}</td>
              <td class="px-6 py-4 text-xs text-neutral-500">{a.lang}</td>
              <td class="px-6 py-4 text-xs font-mono text-neutral-400">{a.views}</td>
              <td class="px-6 py-4">
                <Badge variant={a.status === 'Published' ? 'success' : 'warning'} size="sm">{a.status}</Badge>
              </td>
              <td class="px-6 py-4 text-xs text-neutral-500">{a.date}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    </div>
  </Card>
</PageContainer>
