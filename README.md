## axios.CancelToken

```javascript
import axios from 'axios'
const CancelToken = axios.CancelToken
let cancel = null
export default {
  mounted() {
    this.getData()
  },
  methods: {
    getData() {
      this.axios({
        url: 'http://localhost:9999/list',
        cancelToken: new CancelToken(function executor(c) {
          cancel = c
        })
      })
    }
  },
  beforeDestroy() {
    cancel()
  }
}
```
