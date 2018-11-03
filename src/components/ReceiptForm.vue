<template>
    <div>
        <form @submit.prevent="" class="form-horizontal">
            <fieldset>
                <pre>
                    {{receipt}}
                </pre>

                <!-- Form Name -->
                <div class="form-group row">
                    <legend>Receipt Form</legend>
                </div>
                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-4 control-label text-right" for="txtTitle">Title</label>
                    <div class="col-md-4">
                        <input id="txtTitle" name="txtTitle" v-model="receipt.title" type="text" placeholder="" class="form-control input-md">
                    </div>
                </div>

                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-4 control-label text-right" for="imgurl">Image URL</label>
                    <div class="col-md-4">
                        <input id="imgurl" name="imgurl" v-model="receipt.imgurl" type="text" placeholder="" class="form-control input-md">

                    </div>
                </div>

                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-4 control-label text-right" for="txtDescription">Description</label>
                    <div class="col-md-4">
                        <input id="txtDescription" name="txtDescription" v-model="receipt.description" type="text" placeholder="" class="form-control input-md">

                    </div>
                </div>

                <div class="form-group row">
                    <div class="col-md-4"></div>
                    <div class="col-md-4">
                        <button @click="addIngreadient" class="btn btn-primary float-right"><i class="fa fa-plus-circle"></i> More Ingredient
                        </button>
                        <!-- <button class="btn btn-primary float-right" >More</button> -->
                    </div>

                </div>
                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-4 control-label text-right" for="txtIngredient">Ingredient</label>
                    <div class="col-md-4">
                        <div v-for="(ingredient,index) in receipt.ingredient" :key="index">
                            <input v-model="receipt.ingredient[index]" id="txtIngredient" name="txtIngredient" type="text" placeholder="" class="form-control input-md">
                        </div>
                    </div>
                </div>

                <!-- Button (Double) -->
                <div class="form-group row">
                    <label class="col-md-3 control-label" for="btnSubmit"></label>
                    <div class="col-md-8">
                        <button id="btnSubmit" name="btnSubmit" @click="save" class="btn btn-success">Submit</button>
                        <button id="btnCancel" name="btnCancel" class="btn btn-danger">Cancel</button>
                    </div>
                </div>
            </fieldset>
        </form>
    </div>
</template>

<script>
export default {
    data () {
        return {
            receipt: {
                title: '',
                imgurl: '',
                description: '',
                ingredient: ['']
            }
        }
    },
    methods: {
        addIngreadient () {
            this.receipt.ingredient.push('')
        },
        save(){
            this.$emit('saveReceipt', this.receipt)
        }

    },
}
</script>

<style scoped>
</style>