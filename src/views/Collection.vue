<template>
    <div class="collection">
        <div id="mainContent"> 
            <h1>{{title}}</h1>
            <p>{{description}}</p>
        </div>
        <div id="blockContent">
            <div v-for="(item, index) in blocks" :key="index" :class="[item.value ? 'colorPurple' : 'colorGray']" @click="toggle(index)">
                {{item.value}}
            </div>
        </div>
        <div class="overlay" :style="{ display: modalDisplay }" ref="modal">
            <div class="modal">
                <p>Good job on completing your collection!</p>
                <button id="closeModal" @click="modalDisplay = 'none'">Close</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Collection',
    data() {
        return {
            modalDisplay: 'none',
            title: "Collect all the things!",
            description: "80 days around the world, we’ll find a pot of gold just sitting where the rainbow’s ending. Time — we’ll fight against the time, and we’ll fly on the white wings of the wind. 80 days around the world, no we won’t say a word before the ship is really back. Round, round, all around the world. Round, all around the world. Round, all around the world. Round, all Taround the world.\n\nThundercats are on the move, Thundercats are loose. Feel the magic, hear the roar, Thundercats are loose. Thunder, thunder, thunder, Thundercats! Thunder, thunder, thunder, Thundercats! Thunder, thunder, thunder, Thundercats! Thunder, thunder, thunder, Thundercats! Thundercats!\n\nChildren of the sun, see your time has just begun, searching for your ways, through adventures every day. Every day and night, with the condor in flight, with all your friends in tow, you search for the Cities of Gold. Ah-ah-ah-ah-ah… wishing for The Cities of Gold. Ah-ah-ah-ah-ah… some day we will find The Cities of Gold. Do-do-do-do ah-ah-ah, do-do-do-do, Cities of Gold. Do-do-do-do, Cities of Gold. Ah-ah-ah-ah-ah… some day we will find The Cities of Gold. ",
            blocks: [
                {
                id: "r99yqkuexzf9qa0qaqus5gpan",
                value: 100
                },
                {
                id: "r99yqkuexzf9qa0qaqus5gpan",
                value: 0
                },
                {
                id: "r99yqkuexzf9qa0qaqus5gpan",
                value: 0
                },
                {
                id: "r99yqkuexzf9qa0qaqus5gpan",
                value: 0
                }
            ]
        };
    },
    mounted() {
        window.addEventListener('click', this.closeModal);
    },
    methods: {
        toggle(index) {
            if(this.blocks[index].value === 100) {
                this.blocks[index].value = 0;
            } else {
                this.blocks[index].value = 100;
            }
            if(this.blocks.every(el => el.value === 100)) {
                this.modalDisplay = 'block';
            }
        },
        closeModal(e) {
            if(e.target === this.$refs.modal ? this.modalDisplay = 'none' : 'block');
        }
    },
};
</script>

<style lang="scss" scoped>
    .collection {
        width: 100%;
        min-height: 100%;
        display: grid;
        grid-template-columns: 50% 50%;
        #mainContent {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }
        #blockContent {
            height: 100%;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            div {
                width: 200px;
                height: 200px;
                margin: 15px;
                color: #fff;
                display: flex;
                justify-content: center;
                align-items: center;
            }
        }
        .overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(224, 219, 219, .5);
            z-index: 1;
            transition: all .5s ease;
            .modal {
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                background: rgb(255, 255, 255);
                color: #000;
                padding: 15px;
                border: 1px solid #000;
                z-index: 2;
            }
        }
    }
    
    .colorGray {
        background: rgb(199, 199, 199);
        border: 2px solid rgb(134, 132, 132);
    }
    .colorPurple {
        background: rgb(194, 8, 194);
        border: 2px solid rgb(131, 8, 131);
    }
    @media (max-width: 970px) {
        .collection {
            grid-template-columns: 100%;
        }
    }
</style>