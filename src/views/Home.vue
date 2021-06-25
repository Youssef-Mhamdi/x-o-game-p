<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    
    <div id="game-layout">
      <div class="players left player-1">Mhamdi Youssef</div>
      <div class="players right player-2">Mhamdi Youssef</div>


      <div v-for="slut in sluts" :key="slut" class="vars var-" :class="sluts[slut]" @click="player_1" >{{slut}}</div>

    </div>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'  @click="player_1" 

export default {
  name: 'Home',
  data() {
    return {
      start: null,
      sluts: [1,2,3,4,5,6,7,8,9],
      winner: [ [1,2,3],
                [3,2,1],
                [4,5,6],
                [7,8,9],
                [1,4,7],
                [1,7,4],
                [2,5,8],
                [3,6,9],
                [1,5,9],
                [7,5,3],
                [1,5,4,9],
                [1,4,5,9]
              ],
      player1: [],
      player2: [],


      }
  },
  methods: {
    player_1(e){
      this.start+=1
      var times1 = 0
      var times2 = 0

      if ( this.start %2 ) {
        this.player1.push(e.target.innerText)
        e.target.classList += " bg-red "
        e.target.innerHTML = 'X'
        e.target.disabled = true
        for(var i=0; i< this.winner.length; i++){
          for(var j=0; j<3; j++){
            if (this.winner[i][j] == this.player1[i] ) {
              console.log(  this.winner[i][j] + "- i= "+ i + "-j=" + j + " Matched " +  this.player1[i] )
              times1 += 1
              if (times1 == 3) {
                alert('we have winner - Player 1')
                 location.reload(); 
              }
              break
            }
          }//console.log('Break')
        }
      }else{
        this.player2.push(e.target.innerText)
        e.target.classList += " bg-blue "
        e.target.innerHTML = 'O'
        e.target.disabled = true
        for(var i=0; i< this.winner.length; i++){
          for(var j=0; j<3; j++){
            if (this.winner[i][j] == this.player2[i] ) {
              console.log(  this.winner[i][j] +"- i= "+ i + "-j=" + j + " Match " +  this.player2[i] )
              times2 += 1
              if (times2 == 3) {
                alert('we have winner - Player 2')
              }
            break
            }
            
          }//console.log('Break')
        }
      }
      var times1 = 0
      var times2 = 0
      console.log('----------------------------------------------------------');
      /*
      for(var i=0; i< this.winner.length; i++){
        for(var j=0; j<3; j++){
          if (this.winner[i][j] == this.player1[i] ) {
            console.log(  this.winner[i][j] +"- i= "+ i + "-j=" + j + " Matched " +  this.player1[i] )
            times1 += 1
            if (times1 == 3) {
              alert('we have winner - Player 1')
            }
            break
          }
        }//console.log('Break')
      }
      for(var i=0; i< this.winner.length; i++){
        for(var j=0; j<3; j++){
          if (this.winner[i][j] == this.player2[i] ) {
            console.log(  this.winner[i][j] +"- i= "+ i + "-j=" + j + " Match " +  this.player2[i] )
            times2 += 1
            if (times2 == 3) {
              alert('we have winner - Player 2')
            }
           break
          }
        	
        }//console.log('Break')
      }*/
    //console.log( this.player1 + ' --- VS --- ' + this.player2 )
    //console.log('----------------------------------------------------------');

    },
    player_2(e){
      console.log(e.target)
    }
  }
}



/**[1]
 * 123 * 456 * 789
 * 147 * 258 * 369
 * 159 * 753 
 * for(var i=0; i<winner.length; i++){
 *   for(var j=0; j<3; j++){
 *   	console.log(  winner[i][j]   )
 *   }console.log('Break')
 * }
 */
</script>

<style scoped>
#game-layout {
	height: 630px;
	width: 630px;
	margin: 0 auto;
	display: block;
}
.vars {
	width: 200px;
	height: 200px;
	display: inline-flex;
	border: 2px dotted rgb(146, 61, 108);
  margin: 2px;
  font-size: 12.5rem;
  color: white;
  text-align: center;
}
.bg-red {
  background: rgb(146, 61, 108) !important;
}
.bg-blue {
	background: rgb(0, 0, 0) !important;
}
.right {
	margin: -20px 0 0 70%;
}
.left {
	margin: 0 70% 0 0;
}
</style>