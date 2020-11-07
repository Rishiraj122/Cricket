<template>

    <div class="container" style="text-align: center;">
      <div class="row r1">
        
        <div class="col-lg-6 col-md-12 col-sm-12 name" style="text-align: center">
            <h1 class="firstText">
                <span class="text-wrapper">
                    <span class="letters">Cricket Informer</span>
                </span>
            </h1>
             <h4 style="padding-top: 3%; padding-bottom: 7%">One Place To Get Any Cricket Related Information.</h4>
        </div>

        <div class="col-lg-6 col-md-12 col-sm-12 div1">
          <img src="./gameDay.png" style="width: 100%">
        </div>
        
      </div>
      <div class="row r2">
        <section style="background-color: black; margin: 0 auto; width: 100%">
          <div class="col-lg-12 col-md-12 col-sm-12 div2">
            <input type="text" v-model="search" placeholder="searchbox" />
          </div>
          
          
          <div class="col-lg-12 col-md-12 col-sm-12">
            <div v-for="player in filteredText.slice(0,2)" v-bind:key="player" class="design">
                <p>Cricketer: {{player.Player_Name}} 🏏</p>
                <p>Country: {{player.Country}}, DOB: {{player.DOB}}, Batting_Hand: {{player.Batting_Hand}}, Bowling_Skill: {{player.Bowling_Skill}}</p>
            </div>
          </div>
          
          <div class="col-lg-12 col-md-12 col-sm-12">
            <div v-for="lol in filteredText2.slice(0,1)" v-bind:key="lol" class="design">
                <p>{{lol.team}} 🏆</p>
                <p>Home_wins: {{lol.home_wins}}, Away_wins: {{lol.away_wins}}</p>
                <p>Home_matches: {{lol.home_matches}}, Away_matches: {{lol.away_matches}}</p>
            </div>
          </div>

        </section>
      </div>
    </div>

</template>

<script>


export default {
  name: 'app',
  data(){
    return {
      players: [
         {
            "Player_Name": "A Ashish Reddy",
            "DOB": "24-Feb-91",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm medium",
            "Country": "India"
        },
        {
            "Player_Name": "A Chandila",
            "DOB": "5-Dec-83",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "India"
        },
        {
            "Player_Name": "A Chopra",
            "DOB": "19-Sep-77",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "India"
        },
        {
            "Player_Name": "A Choudhary",
            "Batting_Hand": "Right_hand",
            "Bowling_Skill": "Left-arm fast-medium"
        },
        {
            "Player_Name": "A Dananjaya",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak"
        },
        {
            "Player_Name": "A Flintoff",
            "DOB": "6-Dec-77",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm fast-medium",
            "Country": "England"
        },
        {
            "Player_Name": "A Hales",
            "Batting_Hand": "Right_hand"
        },
        {
            "Player_Name": "A Joseph",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm fast"
        },
        {
            "Player_Name": "A Kumble",
            "DOB": "17-Oct-70",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Legbreak googly",
            "Country": "India"
        },
        {
            "Player_Name": "A Mishra",
            "DOB": "24-Nov-82",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Legbreak",
            "Country": "India"
        },
        {
            "Player_Name": "A Nehra",
            "DOB": "29-Apr-79",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Left-arm medium-fast",
            "Country": "India"
        },
        {
            "Player_Name": "A Symonds",
            "DOB": "9-Jun-75",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "Australia"
        },
        {
            "Player_Name": "MS Dhoni",
            "DOB": "7-Jul-81",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm medium",
            "Country": "India"
        },
        {
            "Player_Name": "VVS Laxman",
            "DOB": "1-Nov-74",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "India"
        },
        {
            "Player_Name": "Virat Kohli",
            "DOB": "5-Nov-98",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm medium",
            "Country": "India"
        },
        {
            "Player_Name": "Yuvraj Singh",
            "DOB": "12-Dec-81",
            "Batting_Hand": "Left_Hand",
            "Bowling_Skill": "Slow left-arm orthodox",
            "Country": "India"
        },
        {
            "Player_Name": "RT Ponting",
            "DOB": "19-Dec-74",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm medium",
            "Country": "Australia"
        },
        {
            "Player_Name": "RR Pant",
            "DOB": "4-Oct-97",
            "Batting_Hand": "Left_Hand",
            "Bowling_Skill": "NULL",
            "Country": "India"
        },
        {
            "Player_Name": "A Symonds",
            "DOB": "9-Jun-75",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "Australia"
        },
        {
            "Player_Name": "B Lee",
            "DOB": "8-Nov-76",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm fast",
            "Country": "Australia"
        },
        {
            "Player_Name": "KD Karthik",
            "DOB": "1-Jun-85",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "NULL",
            "Country": "India"
        },
        {
            "Player_Name": "KL Rahul",
            "DOB": "18-Apr-92",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "NULL",
            "Country": "India"
        },
        {
            "Player_Name": "M Muralitharan",
            "DOB": "17-Apr-72",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "Sri Lanka"
        },
        {
            "Player_Name": "Harbhajan Singh",
            "DOB": "3-Jul-80",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "India"
        },
        {
            "Player_Name": "V Sehwag",
            "DOB": "20-Oct-78",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "India"
        },
        {
            "Player_Name": "Z Khan",
            "DOB": "7-Oct-78",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Left-arm fast-medium",
            "Country": "India"
        },
        {
            "Player_Name": "AD Russell",
            "DOB": "29-Apr-88",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm fast",
            "Country": "West Indies"
        },
        {
            "Player_Name": "A Kumble",
            "DOB": "17-Oct-70",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Legbreak googly",
            "Country": "India"
        },
        {
            "Player_Name": "A Mithun",
            "DOB": "25-Oct-89",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm medium",
            "Country": "India"
        },
        {
            "Player_Name": "A Mukund",
            "DOB": "6-Jan-90",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Legbreak googly",
            "Country": "India"
        },
        {
            "Player_Name": "A Nehra",
            "DOB": "29-Apr-79",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Left-arm medium-fast",
            "Country": "India"
        },
        {
            "Player_Name": "A Nel",
            "DOB": "15-Jul-77",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm fast-medium",
            "Country": "South Africa"
        },
        {
            "Player_Name": "A Roy",
            "Batting_Hand": "Left_Hand",
            "Bowling_Skill": "Slow left-arm orthodox"
        },
        {
            "Player_Name": "A Singh",
            "DOB": "21-Jun-81",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm medium-fast",
            "Country": "India"
        },
        {
            "Player_Name": "A Symonds",
            "DOB": "9-Jun-75",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "Australia"
        },
        {
            "Player_Name": "A Turner",
            "Batting_Hand": "Right_Hand"
        },
        {
            "Player_Name": "A Uniyal",
            "DOB": "21-Nov-81",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Left-arm medium",
            "Country": "India"
        },
        {
            "Player_Name": "A Zampa",
            "DOB": "31-Mar-92",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Legbreak googly",
            "Country": "Australia"
        },
        {
            "Player_Name": "AA Bilakhia",
            "DOB": "31-May-86",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm medium",
            "Country": "India"
        },
        {
            "Player_Name": "AA Chavan",
            "DOB": "28-Oct-85",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Slow left-arm orthodox",
            "Country": "India"
        },
        {
            "Player_Name": "AA Jhunjhunwala",
            "DOB": "1-Dec-82",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm offbreak",
            "Country": "India"
        },
        {
            "Player_Name": "AA Kazi",
            "DOB": "29-Sep-89",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Slow left-arm orthodox",
            "Country": "India"
        },
        {
            "Player_Name": "AA Noffke",
            "DOB": "30-Apr-77",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm fast-medium",
            "Country": "Australia"
        },
        {
            "Player_Name": "AB Agarkar",
            "DOB": "4-Dec-77",
            "Batting_Hand": "Right_Hand",
            "Bowling_Skill": "Right-arm fast",
            "Country": "India"
        }
      ],
      teams: [
    {
        "team": "Rising Pune Supergiant",
        "home_wins": "5",
        "away_wins": "5",
        "home_matches": "8",
        "away_matches": "8",
        "home_win_percentage": "62.5",
        "away_win_percentage": "62.5"
    },
    {
        "team": "Mumbai Indians",
        "home_wins": "58",
        "away_wins": "51",
        "home_matches": "101",
        "away_matches": "86",
        "home_win_percentage": "57.42574257425742",
        "away_win_percentage": "59.30232558139535"
    },
    {
        "team": "Chennai Super Kings",
        "home_wins": "51",
        "away_wins": "49",
        "home_matches": "89",
        "away_matches": "75",
        "home_win_percentage": "57.30337078651685",
        "away_win_percentage": "65.33333333333333"
    },
    {
        "team": "Delhi Capitals",
        "home_wins": "3",
        "away_wins": "7",
        "home_matches": "6",
        "away_matches": "10",
        "home_win_percentage": "50.0",
        "away_win_percentage": "70.0"
    },
    {
        "team": "Sunrisers Hyderabad",
        "home_wins": "30",
        "away_wins": "28",
        "home_matches": "63",
        "away_matches": "45",
        "home_win_percentage": "47.61904761904761",
        "away_win_percentage": "62.22222222222222"
    },
    {
        "team": "Rajasthan Royals",
        "home_wins": "29",
        "away_wins": "46",
        "home_matches": "67",
        "away_matches": "80",
        "home_win_percentage": "43.28358208955223",
        "away_win_percentage": "57.49999999999999"
    },
    {
        "team": "Deccan Chargers",
        "home_wins": "18",
        "away_wins": "11",
        "home_matches": "43",
        "away_matches": "32",
        "home_win_percentage": "41.86046511627907",
        "away_win_percentage": "34.375"
    },
    {
        "team": "Kings XI Punjab",
        "home_wins": "38",
        "away_wins": "44",
        "home_matches": "91",
        "away_matches": "85",
        "home_win_percentage": "41.75824175824176",
        "away_win_percentage": "51.76470588235295"
    },
    {
        "team": "Royal Challengers Bangalore",
        "home_wins": "35",
        "away_wins": "49",
        "home_matches": "85",
        "away_matches": "95",
        "home_win_percentage": "41.17647058823529",
        "away_win_percentage": "51.578947368421055"
    },
    {
        "team": "Kolkata Knight Riders",
        "home_wins": "34",
        "away_wins": "58",
        "home_matches": "83",
        "away_matches": "95",
        "home_win_percentage": "40.963855421686745",
        "away_win_percentage": "61.05263157894737"
    },
    {
        "team": "Delhi Daredevils",
        "home_wins": "25",
        "away_wins": "42",
        "home_matches": "72",
        "away_matches": "89",
        "home_win_percentage": "34.72222222222222",
        "away_win_percentage": "47.19101123595505"
    },
    {
        "team": "Pune Warriors",
        "home_wins": "6",
        "away_wins": "6",
        "home_matches": "20",
        "away_matches": "26",
        "home_win_percentage": "30.0",
        "away_win_percentage": "23.076923076923077"
    },
    {
        "team": "Kochi Tuskers Kerala",
        "home_wins": "2",
        "away_wins": "4",
        "home_matches": "7",
        "away_matches": "7",
        "home_win_percentage": "28.57142857142857",
        "away_win_percentage": "57.14285714285714"
    },
    {
        "team": "Gujarat Lions",
        "home_wins": "1",
        "away_wins": "12",
        "home_matches": "14",
        "away_matches": "16",
        "home_win_percentage": "7.142857142857142",
        "away_win_percentage": "75.0"
    }
],
      search:''
    }
  },
  computed: {
    filteredText: function(){
      return this.players.filter((player)=>{
      return player.Player_Name.toLowerCase().match(this.search.toLowerCase());

      });
    },
    filteredText2: function(){
      return this.teams.filter((lol)=>{
      return lol.team.toLowerCase().match(this.search.toLowerCase());
      });
    }
  }
}


</script>





<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&display=swap');

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.name{
    padding-top: 20%;
    margin-bottom: -5%;
}

.firstText {
  position: relative;
  font-weight: 400;
  font-size: 3em;
  color: navy;
}

.firstText .text-wrapper {
  position: relative;
  display: inline-block;
  padding-top: 0.2em;
  padding-right: 0.05em;
  padding-bottom: 0.1em;
  overflow: hidden;
}

.firstText .letter {
  transform-origin: 50% 100%;
  display: inline-block;
  line-height: 1em;
}


.textBeforeSearch{
    margin-top: -2%;
    padding-bottom: 10%;
    font-family: 'Dancing Script', cursive;
    color: orange;
    font-size: xx-large;
}


input{
  width: 70%;
  text-align: center;
  padding: 1%;
  border: 2px solid black;
}

.div1{
  padding: 5%;
}

section{
  padding: 5%;
}

.div2{
  padding-bottom:5%;
  padding-top: 3%;
}

.r1{
    padding-top: 8%;
}

.r2{
    padding-top: 21%;
  padding-bottom: 7%;
}

.design{
  padding: 3%;
  background-color: blueviolet;
  color: white;
  border-radius: 3%;
  width: 90%;
  margin: 0 auto;
  margin-top: 0.5%;
}

</style>
