<svg id="svg-filter" class="filter hidden">
    <!-- Emerald: `filter: url(#Emerald)` -->
    <filter id="Emerald" filterUnits="objectBoundingBox" primitiveUnits="userSpaceOnUse" color-interpolation-filters="sRGB">

        <!-- RGB, RGB, RGB, 0pacity -->
        <feColorMatrix type="matrix" in="SourceGraphic" result="colormatrix" values="
            .16 .185 .129 0 0
            .16 .185 .129 0 0
            .16 .185 .129 0 0
            0 0 0 0.33 0" />
        
        <feComponentTransfer in="colormatrix" result="componentTransfer">
            <feFuncR type="table" tableValues="0.03 0.9"/>
            <feFuncG type="table" tableValues="0.57 1"/>
            <feFuncB type="table" tableValues="0.49 0.53"/>
            <feFuncA type="table" tableValues="0 1"/>

        </feComponentTransfer>

        <feBlend mode="normal" in="componentTransfer" in2="SourceGraphic" result="blend"/>
    </filter>
</svg>
