<template>
  <div class="px-6 pt-6 sm:pt-8 lg:pt-12 pb-32">
    <article class="prose prose-sm sm:prose lg:prose-lg mx-auto">
      <h1>Setting up Heartcode Web Dev Project</h1>

      <section>
        <div v-if="isMac">
          <h4>Open Terminal (MacOS)</h4>

          <ol class="select-none">
            <li>You can open Terminal by using spotlight with this shortcut: <b>&#8984; + SPACE</b></li>
            <li>And type <b>Terminal</b> in the text field and click enter.</li>
            <li>Type <span class="code">cd ~/Desktop</span> in Terminal and click enter.</li>
            <li>Type <span class="code">npm init heartcode-web-dev</span> in Terminal and click enter.</li>
            <li>The project is now installed in your desktop.</li>
          </ol>
        </div>

        <div v-if="isWindows">
          <h4>Open Command Prompt (Windows)</h4>

          <ol class="select-none">
            <li>You can open Command Prompt with this shortcut: <b>⊞ Win + X</b> followed by <b>C</b></li>
            <li>Type <span class="code">npm config set cache C:\tmp\nodejs\npm-cache --global</span> and click enter.

            <li>
              Type <span class="code">cd Desktop</span> and click enter.
              <ul>
                <li>
                  <small>
                    If you encounter this error:
                    <span class="error-code">The system cannot find the path specified.</span>
                  </small>
                </li>
                <li>
                  <small>You can ignore this step and use your current directory.</small>
                </li>
              </ul>
            </li>

            <li>Type <span class="code">npm init heartcode-web-dev</span> and click enter.</li>
            <li>The project is now installed in your current directory.</li>
          </ol>
        </div>
      </section>

      <h2>Setting up for Development</h2>

      <section>
        <div v-if="isMac">
          <h4>Open Visual Studio Code (MacOS)</h4>

          <ol class="select-none">
            <li>Open Visual Studio Code</li>
            <li>
              Click <b>Open...</b> and find `heartcode-web-dev` folder in your Desktop.
              <img src="@/assets/img/learn/setup/vscode-open-mac.png" alt="Open Project MacOS" class="w-1/2">
            </li>


            <li>
              Open terminal in Visual Studio Code.
              <img src="@/assets/img/learn/setup/vscode-terminal-mac.png" alt="Open VS Code Terminal MacOS" class="w-1/2">
            </li>

            <li>
              Type <span class="code">npm run dev</span> and click enter to run the project.
              <img src="@/assets/img/learn/setup/vscode-terminal-open-mac.png" alt="Npm Run Dev MacOS" class="w-1/2">
            </li>
            <li>
              The project is setup for development!
              You can visit <a target="_blank" href="http://localhost:3000">localhost:3000</a> to try it out yourself.
            </li>
          </ol>
        </div>

        <div v-if="isWindows">
          <h4>Open Visual Studio Code (Windows)</h4>

          <ol class="select-none">
            <li>Open Visual Studio Code</li>
            <li>
              Click <b>Open Folder...</b> and find `heartcode-web-dev` folder in your Desktop.
              <img src="@/assets/img/learn/setup/vscode-open-win.png" alt="Open Project Windows" class="w-1/2">
            </li>

            <li>
              Open terminal in Visual Studio Code.
              <img src="@/assets/img/learn/setup/vscode-terminal-win.png" alt="Open VS Code Terminal Windows" class="w-1/2">
            </li>

            <li>
              Type <span class="code">npm run dev</span> and click enter to run the project.
              <img src="@/assets/img/learn/setup/vscode-terminal-open-win.png" alt="Npm Run Dev Windows" class="w-1/2">
            </li>
            <li>
              The project is setup for development!
              You can visit <a target="_blank" href="http://localhost:3000">localhost:3000</a> to try it out yourself.
            </li>
          </ol>
        </div>
      </section>


      <h2>Installing VSCode Extension</h2>

      <section>
        <ol>
          <li>
            Click
            <a href="vscode:extension/octref.vetur" class="install-ext">
              Install Vetur
            </a>
          </li>

          <li>
            Click
            <a href="vscode:extension/MS-vsliveshare.vsliveshare" class="install-ext">
              Install Live Share
            </a>
          </li>
        </ol>
      </section>


      <h2>Success!</h2>
      <blockquote>
        You would now have <b>Visual Studio Code</b>, <b>Node.js</b> and the <b>heartcode-web-dev</b> project installed.
      </blockquote>
      <n-link to="/learn">
        Go back to /learn
      </n-link>
    </article>
  </div>
</template>

<script>
import OperatingSystemOptions from "~/components/learn/setup/OperatingSystemOptions";

export default {
  components: {OperatingSystemOptions},
  async asyncData({$content}) {
    const page = await $content('learn/setup/installation').fetch()

    return {
      page
    }
  },
  computed: {
    isMac() {
      return navigator.platform.indexOf('Mac') > -1 || this.isNeither
    },
    isWindows() {
      return navigator.platform.indexOf('Win') > -1 || this.isNeither
    },
    isNeither() {
      return navigator.platform.indexOf('Mac') <= -1 && navigator.platform.indexOf('Win') <= -1
    },
  }
}
</script>

<style scoped lang="less">
details:after {
  content: "";
@apply block;
@apply pb-4;
}

summary {
@apply cursor-pointer;

  &:focus {
  @apply outline-none;
  }
}

span.code {
@apply leading-none;
@apply text-gray-900;
@apply bg-gray-300;
@apply px-2;
@apply py-1;
@apply rounded;
@apply font-bold;
@apply select-text;
  font-family: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
}

span.error-code {
@apply text-gray-700;
@apply rounded bg-red-200;
@apply px-2 py-1;
@apply mx-1;
@apply font-medium leading-none text-center;
@apply select-text;
  font-family: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
}

a.install-ext {
  @apply py-2 px-3 rounded bg-gray-300 font-bold text-lg;
  @apply no-underline;
}
</style>
