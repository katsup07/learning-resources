<template>
  <div>
  
          <base-dialog title="Invalid Input" v-if="!inputIsValid" @close="confirmError">
            <template #default>
              All form fields must be filled out.
            </template>
            <template #actions>
              <base-button mode="error-alert" @click="confirmError">Okay</base-button>
            </template>
          </base-dialog>

    <base-card>
      <form @submit.prevent="onSubmitData" action="" @input="confirm">
        <div class="form-group">
          <div class="title">
            <label for="title" >Title</label><!-- Can use ref="..." instead of v-model -->
            <input type="text" id="title" name="title" minlength="0" maxlength="50" ref="title">
          </div>
          <div class="description" minlength="0" maxlength="255">
            <label for="description">Description</label>
            <textarea name="description" id="description" cols="30" rows="5" ref="description"></textarea>
          </div>
          <div class="link">
            <label for="link">Link</label>
            <input type="url" id="link" name="link" placeholder="https://" minlength="0" maxlength="255" ref="link">
          </div>
          <div class="select-box">
              <label for="color">Choose a color </label>
                <select name="color" id="color" ref="color">
                   <option value="purple">purple</option>
                   <option value="blue">blue</option>
                   <option value="green">green</option>
                   <option value="yellow">yellow</option>
                   <option value="orange">orange</option>
                   <option value="pink">pink</option>
                </select>
          </div>
          <div class="add-resource">
            <base-button type="submit">Add Resource</base-button>
          </div>
        </div>
      </form>
  </base-card>
  </div>
</template>
<script>


export default{
  inject:['addResource'],
  
  data(){
    return {
      inputIsValid: true,
    };
  },

  methods: {
    onSubmitData(){
      console.log('submitting in add resource form...')
      // data
      const [title, description, link, class_] = [
        this.$refs.title.value,
        this.$refs.description.value,
        this.$refs.link.value, 
        this.$refs.color.value
      ];
      
      if(this.validateData(title, description, link, class_)){
      this.addResource({ id: title + Date.now(), title, description, link, class: class_});
      }
    },

    // checks data is entered in correct form
    validateData(title, description, link, class_){
      console.log('validating data... ');
      if(title.trim() !== '' && description.trim() !== '' && link.trim() !== '' && class_.trim() !== '' ) 
        return this.inputIsValid = true;
      // else
        return this.inputIsValid = false;
    },
    // confirm having read error message
    confirmError(){
    this.inputIsValid = true
    }
  },
};
</script>

<style scoped>
form {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.1rem;
  max-width: 50vw;
}

label {
    margin: 0.2rem;
    color: rgb(48, 48, 48);
}

textarea {
  resize: none;
}

.title, .description, .link {
   display: flex;
  flex-direction: column;
  margin: 0.2rem;
  width: 45vw;
  font-size: 0.7rem;
  font-weight: 700;
}

.select-box {
  font-size: 0.7rem;
  font-weight: 600;
}

#description {
  font-size: 0.65rem;
}
select#color {
  font-size: 0.6rem;
}
.title input, .description input, .link input{
  font-size: 1em;
}

.add-resource {
  margin-left: 0.2rem;
}

</style>