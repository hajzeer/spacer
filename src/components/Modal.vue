<template>
    <div class="outerWrapper">
        <div class="innerWrapper">
            <div class="photo" v-if="!showMore">
                <img :src="photo" alt="" />
            </div>
            <div class="description" @click="handleShowMore()">
                <h2 class="title">{{ title }}</h2>
                <p class="description" v-if="!showMore">
                    {{ description.slice(0, 200) }}
                </p>
                <span v-if="showMore">
                    {{ description }}
                </span>
            </div>
        </div>
        <div class="close" @click="$emit('closeModal')"/>
    </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },

  data() {
    return {
      photo: null,
      title: null,
      description: null,
      showMore: false,
    };
  },

  mounted() {
    this.photo = this.item.links[0].href;
    this.title = this.item.data[0].title;
    this.description = this.item.data[0].description;
  },

  methods: {
    handleShowMore() {
      this.showMore = true;
    },
  },

};
</script>

<style lang="scss" scoped>
    .outerWrapper {
        background: whitesmoke;
        max-width: 100%;
        height: 100%;
        position: fixed;
        top: 0;
        left: 0;

        @media(min-width: 1024px) {
            max-width: 70%;
            height: 60%;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            margin: auto;
            box-shadow: 0 30px 30px -10px rgba(0, 0, 0, .3);
        }
    }

    .close {
        position: absolute;
        width: 30px;
        height: 30px;
        right: 0;
        top: 0;
        padding: 30px;
        cursor: pointer;

        &::before,
        &::after {
            position: absolute;
            top: 30px;
            right: 20px;
            content: '';
            width: 20px;
            height: 2px;
            background: black;
            display: block;
        }

        &::before {
            transform: rotate(45deg);
        }
        &::after {
            transform: rotate(-45deg);
        }
    }

    .innerWrapper {
        display: flex;
        height: 100%;
        padding: 50px;
        justify-content: center;
        align-items: center;
        flex-direction: column;

        @media (min-width: 1024px) {
            flex-direction: row;

            .photo {
                min-width: 50%;
                margin-right: 20px;
            }

            .description {
                span {
                    font-size: 20px;
                }
            }
        }

        .description {
            color: black;
            cursor: pointer;

            p {
                text-align: justify;
            }

            span {
                font-size: 9px;
            }
        }
        @media (min-width: 1024px) {
            .description {
                span {
                    font-size: 15px;
                }
            }
        }

        .photo {
            width: 100%;
            height: auto;
            background: black;

            img {
                width: 100%;
            }
        }
    }
</style>
