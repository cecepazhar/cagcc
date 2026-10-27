<script lang="ts">
  export let size: number | string = 28;
  export let className: string = '';
</script>

<svg
  width={size}
  height={size}
  viewBox="0 0 512 512"
  class="shrink-0 {className}"
  xmlns="http://www.w3.org/2000/svg"
>
  <defs>
    <linearGradient id="gccShieldGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#10B981" />
      <stop offset="100%" stop-color="#3B82F6" />
    </linearGradient>
    <radialGradient id="gccGlow" cx="50%" cy="50%" r="50%">
      <stop offset="0%" stop-color="#3B82F6" stop-opacity="0.25" />
      <stop offset="100%" stop-color="#3B82F6" stop-opacity="0" />
    </radialGradient>
  </defs>
  <!-- Background squircle -->
  <rect x="24" y="24" width="464" height="464" rx="112" fill="#0A0A0C" stroke="#3B82F6" stroke-width="4" stroke-opacity="0.3"/>
  <!-- Radial glow -->
  <circle cx="256" cy="256" r="210" fill="url(#gccGlow)"/>
  <!-- Cryptographic Shield & Single Globe Ring -->
  <g fill="none">
    <path d="M256 84 L396 136 C396 288 272 404 256 428 C240 404 116 288 116 136 Z"
          stroke="url(#gccShieldGrad)" stroke-width="28" stroke-linecap="round" stroke-linejoin="round"/>
    <circle cx="256" cy="232" r="68" stroke="#10B981" stroke-width="26"/>
    <ellipse cx="256" cy="232" rx="28" ry="68" stroke="#34D399" stroke-width="26"/>
  </g>
</svg>
