<template>
  <div class="keys">
    <div data-key="65" class="key" :class="{ playing: playing == 65 }">
      <kbd>A</kbd>
      <span class="sound">clap</span>
    </div>
    <div data-key="83" class="key" :class="{ playing: playing == 83 }">
      <kbd>S</kbd>
      <span class="sound">hihat</span>
    </div>
    <div data-key="68" class="key" :class="{ playing: playing == 68 }">
      <kbd>D</kbd>
      <span class="sound">kick</span>
    </div>
    <div data-key="70" class="key" :class="{ playing: playing == 70 }">
      <kbd>F</kbd>
      <span class="sound">openhat</span>
    </div>
    <div data-key="71" class="key" :class="{ playing: playing == 71 }">
      <kbd>G</kbd>
      <span class="sound">boom</span>
    </div>
    <div data-key="72" class="key" :class="{ playing: playing == 72 }">
      <kbd>H</kbd>
      <span class="sound">ride</span>
    </div>
    <div data-key="74" class="key" :class="{ playing: playing == 74 }">
      <kbd>J</kbd>
      <span class="sound">snare</span>
    </div>
    <div data-key="75" class="key" :class="{ playing: playing == 75 }">
      <kbd>K</kbd>
      <span class="sound">tom</span>
    </div>
    <div data-key="76" class="key" :class="{ playing: playing == 76 }">
      <kbd>L</kbd>
      <span class="sound">tink</span>
    </div>

  <!--     <audio data-key="65" src="/static/sounds/clap.wav"></audio>
      <audio data-key="83" src="/static/sounds/hihat.wav"></audio>
      <audio data-key="68" src="/static/sounds/kick.wav"></audio>
      <audio data-key="70" src="/static/sounds/openhat.wav"></audio>
      <audio data-key="71" src="/static/sounds/boom.wav"></audio>
      <audio data-key="72" src="/static/sounds/ride.wav"></audio>
      <audio data-key="74" src="/static/sounds/snare.wav"></audio>
      <audio data-key="75" src="/static/sounds/tom.wav"></audio>
      <audio data-key="76" src="/static/sounds/tink.wav"></audio> -->
  </div>
</template>

<script>
export default {
  name: 'Drum',
  data () {
    return {
      playing: null,
    }
  },
  created() {
    this.onKeyDown = this.onKeyDown.bind(this);
    this.onKeyUp = this.onKeyUp.bind(this);
    document.addEventListener('keydown', this.onKeyDown);
    document.addEventListener('keyup', this.onKeyUp);
  },
  destroyed() {
    document.removeEventListener('keydown', this.onKeyDown);
    document.removeEventListener('keyup', this.onKeyUp);
  },
  methods: {
    playSound (sound) {
      console.log("sound", sound);
      if(sound) {
        var audio = new Audio(sound);
        audio.currentTime = 0;
        audio.play();
      }
    },
    onKeyUp(e) {
      this.playing = null;
    },
    onKeyDown(e) {
      const path = "/static/sounds/";
      console.log (path + "clap.wav");
      
      switch (e.keyCode) {
        case 65 : this.playSound(path + "clap.wav"); this.playing = 65 ; break; // 
        case 83 : this.playSound(path + "hihat.wav"); this.playing = 83 ; break;
        case 68 : this.playSound(path + "kick.wav"); this.playing = 68 ; break;
        case 70 : this.playSound(path + "openhat.wav"); this.playing = 70 ; break;
        case 71 : this.playSound(path + "boom.wav"); this.playing = 71 ; break;
        case 72 : this.playSound(path + "ride.wav"); this.playing = 72 ; break;
        case 74 : this.playSound(path + "snare.wav"); this.playing = 74 ; break;
        case 75 : this.playSound(path + "tom.wav"); this.playing = 75 ; break;
        case 76 : this.playSound(path + "tink.wav"); this.playing = 76 ; break;

      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.keys {
  display:flex;
  flex:1;
  min-height:100vh;
  align-items: center;
  justify-content: center;
}

.key {
  border:4px solid black;
  border-radius:5px;
  margin:1rem;
  font-size: 1.5rem;
  padding:1rem .5rem;
  transition:all .07s;
  width:100px;
  text-align: center;
  color:white;
  background:rgba(0,0,0,0.4);
  text-shadow:0 0 5px black;
}

.playing {
  transform:scale(1.1);
  border-color:#ffc600;
  box-shadow: 0 0 10px #ffc600;
}

kbd {
  display: block;
  font-size: 40px;
}

.sound {
  font-size: 1.2rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  color:#ffc600;
}

</style>
