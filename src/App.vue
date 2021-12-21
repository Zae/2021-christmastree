<template>
    <section class="tree">
        <div class="lights">
            <span
                v-for="(e, i) in els"
                :class="`light light--${color()} light--${blink()} light${i}`"
            />
        </div>
        <div class="branches">
            <div
                v-for="(e, i) in branches"
                :class="`branch branch--lvl${i}`"
            />
        </div>
        <div class="balls">
            <span
                v-for="(e, i) in balls"
                :class="`ball ball--${color()} ball${i}`"
            />
        </div>
        <div class="stump" />
        <div class="presents">
            <span
                v-for="(e, i) in presents"
                :class="`present present--${presentColor()} present${i} ribbon ribbon--${presentColor()} present--${presentShape()}`"
            />
        </div>
    </section>
</template>

<script>
const colors = ['blue', 'red', 'yellow', 'white', 'purple', 'gold'];
const presentColors = ['blue', 'red', 'yellow', 'purple', 'gold'];
const blinks = ['blink1', 'blink2', 'blink3', 'blink4', 'blink5', 'blink6', 'blink7', 'blink8', 'blink9'];
const presentShapes = ['portrait', 'landscape', 'square'];

const MAX_BLINK = 2000;

export default {
    data() {
        return {
            nBranches: 6,
            nLights: 299,
            nBalls: 21,
            nPresents: 7,
            rand1: this.rand(MAX_BLINK),
            rand2: this.rand(MAX_BLINK),
            rand3: this.rand(MAX_BLINK),
            rand4: this.rand(MAX_BLINK),
            rand5: this.rand(MAX_BLINK),
            rand6: this.rand(MAX_BLINK),
            rand7: this.rand(MAX_BLINK),
            rand8: this.rand(MAX_BLINK),
            rand9: this.rand(MAX_BLINK),
        };
    },
    computed: {
        branches() { return Array(this.nBranches).fill(!!1); },
        els()      { return Array(this.nLights).fill(!!1);   },
        balls()    { return Array(this.nBalls).fill(!!1);    },
        presents() { return Array(this.nPresents).fill(!!1); }
    },
    methods: {
        rand(max, min = 0)      { return Math.random() * (max - min) + min; },
        getRandFromArray(list)  { return list[Math.floor(this.rand(0, list.length))]; },
        color()                 { return this.getRandFromArray(colors); },
        presentColor()          { return this.getRandFromArray(presentColors); },
        presentShape()          { return this.getRandFromArray(presentShapes); },
        blink()                 { return this.getRandFromArray(blinks);},
    }
}
</script>

<style lang="less">
.tree {
    .square(29em);

    overflow: hidden;
}

.branch {       .arrow-up(2em);     transform: translateY(0em)      translateX(12em);   }
.branch--lvl1 { .arrow-up(4em);     transform: translateY(-1em)     translateX(10em);   }
.branch--lvl2 { .arrow-up(8em);     transform: translateY(-4em)     translateX(6em);    }
.branch--lvl3 { .arrow-up(12em);    transform: translateY(-10em)    translateX(2em);    }
.branch--lvl4 { .arrow-up(12em);    transform: translateY(-19em)    translateX(2em);    }
.branch--lvl5 { .arrow-up(12em);    transform: translateY(-29em)    translateX(2em);    }

.stump {
    .square(40px; 50px);

    background-color: saddlebrown;
    transform: translateY(-29em) translateX(13em)
}

.lights   { position: absolute; z-index: 1; top: 10px; left: 7.5px; }
.balls    { position: absolute; z-index: 2; top: 0;    left: 0;     }
.presents { position: absolute; z-index: 3; top: 0;    left: 0;     }

@lights-list: {
    0: 222px, 05px;
    1: 214px, 09px;
    2: 235px, 15px;
    3: 225px, 21px;
    4: 210px, 27px;
    5: 200px, 29px;
    6: 220px, 33px;
    7: 240px, 36px;
    8: 247px, 41px;
    9: 260px, 43px;
    10: 253px, 45px;
    11: 243px, 45px;
    12: 233px, 42px;
    13: 222px, 35px;
    14: 212px, 35px;
    15: 198px, 28px;
    16: 188px, 18px;
    17: 178px, 19px;
    18: 185px, 22px;
    19: 194px, 21px;
    20: 203px, 18px;
    21: 214px, 13px;
    22: 224px, 5px;
    23: 232px, 5px;
    24: 240px, 5px;
    25: 250px, 0px;
    26: 258px, 0px;
    27: 267px, -12px;
    28: 276px, -22px;
    29: 285px, -20px;
    30: 295px, -20px;
    31: 299px, -15px;
    32: 296px, -11px;
    33: 286px, -11px;
    34: 278px, -13px;
    35: 269px, -20px;
    36: 259px, -27px;
    37: 249px, -30px;
    38: 240px, -38px;
    39: 232px, -45px;
    40: 223px, -53px;
    41: 211px, -60px;
    42: 201px, -63px;
    43: 192px, -63px;
    44: 182px, -67px;
    45: 173px, -74px;
    46: 164px, -80px;
    47: 155px, -80px;
    48: 147px, -82px;
    49: 143px, -78px;
    50: 150px, -77px;
    51: 158px, -85px;
    52: 167px, -85px;
    53: 174px, -87px;
    54: 183px, -87px;
    55: 191px, -87px;
    56: 199px, -94px;
    57: 208px, -100px;
    58: 217px, -108px;
    59: 226px, -114px;
    60: 234px, -123px;
    61: 243px, -130px;
    62: 252px, -132px;
    63: 260px, -132px;
    64: 268px, -139px;
    65: 276px, -149px;
    66: 284px, -151px;
    67: 292px, -160px;
    68: 302px, -160px;
    69: 311px, -160px;
    70: 318px, -159px;
    71: 325px, -159px;
    72: 328px, -156px;
    73: 322px, -152px;
    74: 312px, -152px;
    75: 303px, -154px;
    76: 294px, -157px;
    77: 285px, -164px;
    78: 278px, -172px;
    79: 270px, -180px;
    80: 262px, -189px;
    81: 254px, -198px;
    82: 245px, -206px;
    83: 237px, -211px;
    84: 228px, -214px;
    85: 220px, -216px;
    86: 212px, -220px;
    87: 204px, -220px;
    88: 197px, -220px;
    89: 190px, -228px;
    90: 182px, -236px;
    91: 174px, -246px;
    92: 165px, -248px;
    93: 157px, -250px;
    94: 150px, -252px;
    95: 144px, -260px;
    96: 137px, -264px;
    97: 130px, -273px;
    98: 121px, -281px;
    99: 113px, -285px;
    100: 106px, -283px;
    101: 110px, -282px;
    102: 117px, -281px;
    103: 124px, -281px;
    104: 132px, -281px;
    105: 140px, -282px;
    106: 147px, -282px;
    107: 154px, -289px;
    108: 161px, -297px;
    109: 170px, -306px;
    110: 178px, -306px;
    111: 187px, -306px;
    112: 195px, -306px;
    113: 203px, -314px;
    114: 211px, -322px;
    115: 219px, -330px;
    116: 227px, -338px;
    117: 236px, -338px;
    118: 244px, -340px;
    119: 252px, -340px;
    120: 260px, -345px;
    121: 268px, -354px;
    122: 276px, -364px;
    123: 285px, -368px;
    124: 292px, -368px;
    125: 300px, -368px;
    126: 307px, -375px;
    127: 314px, -384px;
    128: 322px, -392px;
    129: 330px, -395px;
    130: 336px, -395px;
    131: 342px, -397px;
    132: 348px, -397px;
    133: 355px, -395px;
    134: 350px, -392px;
    135: 341px, -392px;
    136: 332px, -390px;
    137: 323px, -392px;
    138: 315px, -402px;
    139: 307px, -412px;
    140: 299px, -420px;
    141: 293px, -420px;
    142: 285px, -418px;
    143: 277px, -417px;
    144: 270px, -417px;
    145: 263px, -424px;
    146: 256px, -432px;
    147: 248px, -440px;
    148: 240px, -448px;
    149: 233px, -458px;
    150: 225px, -466px;
    151: 217px, -469px;
    152: 210px, -469px;
    153: 203px, -469px;
    154: 196px, -469px;
    155: 189px, -470px;
    156: 181px, -478px;
    157: 173px, -486px;
    158: 164px, -495px;
    159: 157px, -504px;
    160: 149px, -513px;
    161: 141px, -521px;
    162: 134px, -529px;
    163: 127px, -538px;
    164: 120px, -540px;
    165: 113px, -541px;
    166: 106px, -541px;
    167: 98px, -541px;
    168: 93px, -538px;
    169: 95px, -534px;
    171: 100px, -537px;
    172: 107px, -537px;
    173: 115px, -543px;
    174: 122px, -550px;
    175: 129px, -560px;
    176: 136px, -570px;
}

@random-numbers: {
    1: v-bind(rand1);
    2: v-bind(rand2);
    3: v-bind(rand3);
    4: v-bind(rand4);
    5: v-bind(rand5);
    6: v-bind(rand6);
    7: v-bind(rand7);
    8: v-bind(rand8);
    9: v-bind(rand9);
}

@colors: {
    0: red;
    1: blue;
    2: white;
    3: yellow;
    4: purple;
    5: gold;
}

@present-colors: {
    0: red;
    1: blue;
    3: yellow;
    4: purple;
    5: gold;
}

.arrow-up(@width; @color: darkgreen) {
    width: 0;
    height: 0;

    border-left: @width solid transparent;
    border-right: @width solid transparent;
    border-bottom: @width solid @color;
}

.arrow-up(@width; @width2; @color: darkgreen) {
    width: 0;
    height: 0;

    border-left: @width solid transparent;
    border-right: @width solid transparent;
    border-bottom: @width2 solid @color;
}

.blink(@animation, @time, @repeat) {
    background-color: transparent;
    animation: @animation @time ease-in-out @repeat;
}

.light {
    .square(5px);

    each(@lights-list, {
        &.light@{key} { transform: translate(@value); }
    });

    each(@random-numbers, {
        &.light--blink@{key} { animation-delay: calc(1ms * @value) !important; }
    });

    each(@colors, {
        @keyframes ~'blink-@{value}' { .blink-animation(@value); }
        &.light--@{value} { .blink(~'blink-@{value}', 2.5s, infinite); }
    });
}

@balls-list: {
    0: 244px, 55px;
    1: 210px, 66px;
    2: 169px, 90px;
    3: 275px, 70px;
    4: 190px, 126px;
    5: 228px, 109px;
    6: 298px, 133px;
    7: 144px, 110px;
    8: 160px, 141px;
    9: 248px, 121px;
    10: 351px, 114px;
    11: 92px, 107px;
    12: 252px, 135px;
    13: 182px, 122px;
    14: 101px, 105px;
    15: 366px, 130px;
    16: 120px, 115px;
    17: 162px, 115px;
    18: 223px, 100px;
    19: 292px, 91px;
    20: 78px, 72px;
    21: 0px, 0px;
    22: 0px, 0px;
    23: 0px, 0px;
}

.ball {
    .square(10px);
    .round();

    margin-top: 2px;

    &::before {
        .square(3px);

        content: '';
        position: relative;

        top: -2px;
        left: 3.6px;
    }

    each(@balls-list, {
        &.ball@{key} { transform: translate(@value); }
    });

    each(@colors, {
        &.ball--@{value} { background-color: @value; }
        &.ball--@{value}::before { background-color: @value; }
    });
}

@present-list: {
    0: 240px, 371px;
    1: 190px, 350px;
    2: 230px, 330px;
    3: 270px, 300px;
    4: 80px, 260px;
    5: 90px, 240px;
    6: 340px, 190px;
}

@present-shapes: {
    0: portrait;
    1: landscape;
    2: square;
}

.present-shape(portrait)  { .square(32px; 38px); }
.present-shape(landscape) { .square(38px; 32px); }
.present-shape(square)    { .square(32px); }

.ribbon-shape-before(portrait)  { .square(32px; 4px); }
.ribbon-shape-before(landscape) { .square(38px; 4px); }
.ribbon-shape-before(square)    { .square(32px; 4px); }

.ribbon-shape-after (portrait)  { .square(4px; 38px); }
.ribbon-shape-after (landscape) { .square(4px; 32px); }
.ribbon-shape-after (square)    { .square(4px; 32px); }

.present {
    position: relative;

    each(@present-colors, {
        &.present--@{value} { background-color: @value; }
    });

    each(@present-list, {
        &.present@{key} { transform: translate(@value); }
    });

    each(@present-shapes, {
        &.present--@{value} { .present-shape(@value); }
    });

    &.ribbon {
        &::before, &::after {
            content: '';
            position: absolute;
            left: 0;
            top: 0;

            each(@present-colors, {
                .ribbon--@{value}& { background-color: @value; }
            });
        }

        &::before {
            transform: translateY(14px);

            each(@present-shapes, {
                .present--@{value}& { .ribbon-shape-before(@value); }
            });
        }

        &::after {
            transform: translateX(17px);

            each(@present-shapes, {
                .present--@{value}& { .ribbon-shape-after(@value); }
            });
        }
    }
}

.blink-animation(@color: red) {
    from {  background-color: transparent;  }
    10% {   background-color: @color;       }
    80% {   background-color: @color;       }
    to {    background-color: transparent;  }
}

.square(@size) { .square(@size; @size); }
.square(@width; @height) {
    display: block;
    width: @width;
    height: @height;
}
.round() { border-radius: 50%; }

.star() {
    .square(0);

    margin: 50px 0;
    position: relative;
    color: gold;

    border-right: 100px solid transparent;
    border-left: 100px solid transparent;
    border-bottom: 70px solid gold;

    transform: rotate(35deg);

    &::before {
        .square(0);

        border-left: 30px solid transparent;
        border-right: 30px solid transparent;
        border-bottom: 80px solid gold;

        position: absolute;
        top: -45px;
        left: -65px;
        content: '';
        transform: rotate(-35deg);
    }

    &::after {
        .square(0);

        position: absolute;
        color: red;
        top: 3px;
        left: -105px;

        border-right: 100px solid transparent;
        border-left: 100px solid transparent;
        border-bottom: 70px solid gold;

        transform: rotate(-70deg);
        content: '';
    }
}
</style>
