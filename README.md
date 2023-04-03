import axios from "axios";

const instance = axios.create({
  baseURL: "http://localhost:4545/api/v1",
  headers: {
    Authorization: `Bearer ${"YOUR_ACCESS_TOKEN"}`,
  },
});

class axiosHttp {
  async getInstance(body = "/") {
    return await instance.get(`/admin` + body);
  }

  // axios.delete(`http://localhost:8001/persons/${id}`)

  async PostInstance(path = "/", body) {
    return await instance.post(`/admin` + path, body);
  }

  async DeleteInstance(id) {
    return await instance.delete(`/admin/` + id);
  }

  //   axios
  //   .patch('https://jsonplaceholder.typicode.com/posts/1', userToPatch)

  async patchInstance(id, body) {
    return await instance.patch(`/admin/` + id, body);
  }
}

export default new axiosHttp();
