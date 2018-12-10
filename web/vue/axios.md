#   npm install axios

#   ��Ӧ�ṹ

    {
      data: {},             // �ɷ������ṩ����Ӧ
      status: 200,          // ���Է�������Ӧ�� HTTP ״̬��
      statusText: 'OK',     // ���Է�������Ӧ�� HTTP ״̬��Ϣ
      headers: {},          // ��������Ӧͷ
      config: {}            // Ϊ�����ṩ��������Ϣ
    }
    
    --->  then(function(response) { ... })
    
#   get

    // Ϊ���� ID �� user ��������/user?id=12345
    axios.get('/user', {
        params: {
          id: 12345
        }
      })
      .then(function (response) {
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });   
      
    // or
    axios.get('/user?id=12345')
      .then(function (response) {
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });

      
#   POST ����

    axios.post('/user', {
        firstName: 'Fred',
        lastName: 'Flintstone'
      })
      .then(function (response) {
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });

#   ����������󣬶���ɺ�ż������� then()��

    function getUserAccount() {
      return axios.get('/user/12345');
    }
    
    function getUserPermissions() {
      return axios.get('/user/12345/permissions');
    }
    
    axios.all([getUserAccount(), getUserPermissions()])
      .then(axios.spread(function (acct, perms) {
        // �����������ڶ�ִ�����
      }));




#	����















