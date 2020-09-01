<template>
<div>
    <img :src="Logo" width="800" height="280" class="img-fluid mx-auto">
    <br />
    <br />
    <br />
    <button v-on:click="randomHero" class="btn btn-secondary">Start</button><p></p>
    <button v-on:click="attack" class="btn btn-danger mb-4">Attack</button>
    <button v-on:click="special" class="btn btn-warning mb-4">SpecialAttack</button>
    <button class="btn btn-info mb-4" @click.prevent="playSound('https://x2convert.com/th/Thankyou?token=U2FsdGVkX18lICc2WZ1gvMESLpeZtDk7BeYwa0QJxoPUn4a%2fTBg5RufGw97b%2fLeE2PITa3xjirRyVTn1b8uc%2b543VccYADK6Tgc4fMbGbTaRe1yDx6L61OBuPqfZV1pT%2fwf9MUa5XT4cvrQUpB35QfQIAQKae7ADJayKjDdQsmU%3d&s=youtube&id=&h=5048920861420491537')"><span class="fa fa-play-circle-o"></span>Music</button><p></p>
    <div class="contianer">
        <div class="row">
            <div class="col-4">
                Name : {{NameHero}}
                <br />
                <img :src="ImgHero" :height="HPHero" class="mx-auto" />
                <br>
                HP : {{HPHero}}
                <br>
                <img v-bind:style="{width : HPHero + 'px'}" :src="BloodHero" alt height="25px" class=" mx-auto" />
            </div>
            <div class="col-4">
                <img :src="ImgF" width="500" height="200" class="img-fluid mx-auto">
                <img :src="ImgWin" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgDraw" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgLose" class="img-fluid mx-auto" width="500" height="200" />
            </div>
            <div class="col-4">
                Name : {{NameMonster}}
                <br />
                <img :src="ImgMonster" :height="HPMonster" class="mx-auto" />
                <br>
                HP : {{HPMonster}}
                <br>
                <img v-bind:style="{width : HPMonster + 'px'}" :src="BloodMonster" alt height="25px" class=" mx-auto" />
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            BloodHero: "https://cdn.discordapp.com/attachments/746260527235334237/748860632693997595/BloodHero.png",
            BloodMonster: "https://cdn.discordapp.com/attachments/746260527235334237/748860627560300544/BloodMonster.png",
            Hero: "",
            Monster: "",
            NameHero: "",
            NameMonster: "",
            HPHero: "",
            HPMonster: "",
            SPATKHero: "",
            SPATKMonster: "",
            ATKHero: "",
            ATKMonster: "",
            ImgWin: "https://cdn.discordapp.com/attachments/746260527235334237/748568823937892433/WIN0.png",
            ImgLose: "https://cdn.discordapp.com/attachments/746260527235334237/748568813561315328/LOSE0.png",
            ImgDraw: "https://cdn.discordapp.com/attachments/746260527235334237/748568804375920640/DRAW0.png",
            Logo: "https://lh3.googleusercontent.com/htQ_76q4ARQS2t75_tAtQHve0X0RHO2_VnaKgNkW3uBT66F0YU9VCnJeTUy3erI_dVr9",
            Win: "https://cdn.discordapp.com/attachments/746260527235334237/748568823937892433/WIN0.png",
            Lose: "https://cdn.discordapp.com/attachments/746260527235334237/748568813561315328/LOSE0.png",
            Draw: "https://cdn.discordapp.com/attachments/746260527235334237/748568804375920640/DRAW0.png",
            ImgF: 'https://cdn.discordapp.com/attachments/746260527235334237/748568792455708872/FIGHT0.png',
            player: [{
                name: 'ชินจัง',
                hp: 800,
                image: 'https://pbs.twimg.com/profile_images/1093909062448640001/P0ba1oea_400x400.jpg'
            }, {
                name: 'เนเน่จัง',
                hp: 700,
                image: 'https://img.online-station.net/_content/2018/1122/gallery/1542865518.png'
            }, {
                name: 'คาซาม่าคุง',
                hp: 850,
                image: 'https://img.online-station.net/_content/2018/1122/gallery/1542865512.png'
            }, {
                name: 'โบจัง',
                hp: 875,
                image: 'https://img.online-station.net/_content/2018/1122/gallery/1542865539.png'
            }, {
                name: 'มาซาโอะคุง',
                hp: 800,
                image: 'https://img.online-station.net/_content/2018/1122/gallery/1542865533.png'
            },],
            monster: [{
                name: 'แฮมทาโร่',
                hp: 850,
                image: 'https://stickershop.line-scdn.net/stickershop/v1/product/866/LINEStorePC/main.png;compress=true'
            }, {
                name: '	ลาปิส',
                hp: 800,
                image: 'https://sites.google.com/site/thehamtarogang/_/rsrc/1430301830175/home/character/oharahome/Lapiss.png'
            }, {
                name: 'แพนด้าคุง',
                hp: 800,
                image: 'https://2.bp.blogspot.com/-5D6BMdyecNo/TyTihvugqaI/AAAAAAAAABI/CHI3Slgc998/s280/hamtaro_g_006.gif'
            }, {
                name: 'พี่โย่ง',
                hp: 850,
                image: 'https://pbs.twimg.com/media/D09ljMEVAAAXHMC.jpg'
            }, {
                name: 'พี่แว่น',
                hp: 700,
                image: 'https://image.dek-d.com/23/2443943/104924807'
            }, ]
        }
    },
    methods: {
        randomHero: function () {
            this.Hero = Math.max(Math.floor(Math.random() * this.player.length));
            this.Monster = Math.max(Math.floor(Math.random() * this.monster.length));
            this.HPHero = this.player[this.Hero].hp
            this.HPMonster = this.monster[this.Monster].hp
            this.NameHero = this.player[this.Hero].name
            this.NameMonster = this.monster[this.Monster].name
            this.ImgHero = this.player[this.Hero].image
            this.ImgMonster = this.monster[this.Monster].image
            this.ImgWin = "";
            this.ImgLose = "";
            this.ImgDraw = "";
        },
        attack: function () {
            this.ATKHero = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            this.ATKMonster = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.ATKMonster;
            }
            if (this.HPMonster != 0 && this.HPHero != 0) {
                this.HPMonster -= this.ATKHero;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        special: function () {
            this.SPATKHero = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            this.SPATKMonster = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPMonster -= this.SPATKHero;
            }
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.SPATKMonster;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        playSound(sound) {
            if (sound) {
                var audio = new Audio(sound);
                audio.play();
            }
        }
    }
}
</script>


<style>
body {
    font-family: 'Russo One', sans-serif;
}
</style>