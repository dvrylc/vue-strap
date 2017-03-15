<template>
    <div class="question-wrapper">
        <div class="body-wrapper">
            <!-- Default slot is question body -->
            <slot></slot>
            <div v-if="hasInput" class="textarea-container">
                <div><strong>You can write your answer in the box below.</strong></div>
                <textarea class="form-control question-input" rows="3"></textarea>
            </div>
        </div>
        <accordion>
            <panel header="Hint" expandable>
                <slot name="hint">
                    No hint is available for this question.
                </slot>
            </panel>
            <panel header="Answer" expandable>
                <slot name="answer"></slot>
            </panel>
        </accordion>
    </div>
</template>

<script>
  import {coerce} from './utils/utils.js'
  import morph from './Morph.vue'
  import accordion from './Accordion.vue'
  import panel from './Panel.vue'

  export default {
    components: {
      panel,
      morph,
      accordion
    },
    props: {
      hasInput: {
        type: Boolean,
        coerce: coerce.boolean,
        default: false
      }
    }
  }
</script>

<style>
    .textarea-container {
        margin: 8px 0;
    }
    .textarea-container > textarea {
        margin: 4px 0;
    }
</style>