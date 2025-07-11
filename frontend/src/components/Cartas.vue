<template>
    <div class="perspective-midrange flex justify-center">
        <div class="relative w-98 h-74 duration-500 transform-3d transition-transform hover:[transform:rotate3d(-1,1,0,180deg)] -rotate-45">
            <div class="cinzel tracking-wider absolute w-full h-full backface-hidden bg-gray-500 text-white rounded-2xl flex items-center justify-center shadow-2xl text-4xl">
                Fluent Flip
            </div>

            <div class="cinzel absolute w-full h-full backface-hidden bg-slate-700 text-white rounded-2xl justify-center shadow-2xl transform rotate-y-180 flex flex-col items-center">
                <h1 class="text-4xl">Fluent Flip</h1>   <!-- TODO: change language of fluent flip on each flip -->
                <p class="text-lg">Developed by <a href="https://adrianceballos.com" target="_blank" rel="noopener" class="text-blue-300">Adrian</a></p>
            </div>
        </div>
    </div>
</template>