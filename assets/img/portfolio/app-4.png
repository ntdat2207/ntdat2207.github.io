(function() {
  "use strict";
  $(document).ready(function() {
    $("#send-message").click(function () {
      const name = $('#name-field').val();
      const email = $('#email-field').val();
      const message = $('#message-field').val();
      if (!name || !email || !message) {
        alert('Vui lòng điền đầy đủ thông tin.');
        return;
      }
      showLoading();
      $.ajax({
        url: 'https://n8n.baokim.vn/webhook/7087aff8-40fe-422c-a2f3-0d075dcc71ce',
        type: 'POST',
        data: {
          name: name,
          email: email,
          chat: message
        },
        headers: {
          'api_key': '4yx1HkvovaE54FPeCYj8KyYkx94nX3lsga6H63iEjvMRjhf1NOIPxcBCA8JJw0m5',
        },
        success: function (response) {
          appendUserMessage();
          console.log('Thành công:', response);
          appendBotMessage(response[0].output);
        },
        error: function (xhr, status, error) {
          console.log('Lỗi:');
          console.log(error);
          appendUserMessage();
          appendBotMessage('Đã có lỗi xảy ra, vui lòng thử lại sau.');
        }
      }).always(function () {
        hideLoading();
        scrollChat();
      })
    });

    function showLoading() {
      $('#loading').css({
        'display': 'flex'
      })
    }

    function hideLoading() {
      $('#loading').css({
        'display': 'none'
      })
    }

    function appendUserMessage() {
      const userMessage = $('#message-field').val();
      if (userMessage) {
        let message = '<div class=\"bg-light text-dark p-2 rounded mb-2 align-self-start w-75\">';
        message += userMessage;
        message += '</div>';
        $('#chat-box').append(message);
        $('#message-field').val('');
      }
    }

    function appendBotMessage(message) {
      let botMessage = '<div class="bg-primary text-white p-2 rounded mb-2 align-self-end w-75">';
      botMessage += message;
      botMessage += '</div>';
      $('#chat-box').append(botMessage);
    }

    function scrollChat() {
      const container = $('#chat-scroll-container');
      container.scrollTop(container[0].scrollHeight);
    }
  });
})();