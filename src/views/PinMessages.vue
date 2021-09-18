<template>
    <div class="">
        <h2>Pin Message</h2>
        <!-- Pinned Counter -->
        <div class="pinned-info d-inline-flex align-items-center mb-3 px-3 py-1">
        <div class="me-1"><img src="../assets/pin.png" alt="Pin photo"></div>
        <div><span>{{counter}}</span> Pinned</div>
        </div>

        <div class="pin-block px-2 py-2 mb-3">            
            <div  v-for="(message) in messageList" :key="message.sender">
                <!-- Pinned block -->
                <div class="d-flex align-items-center mb-1">
                    <div v-if="message.pinned" class="pin-image-box d-flex justify-content-end me-3">
                    <img class="d-inline" src="../assets/pin.png" alt="Pin photo" />
                    </div>
                    <div v-if="message.pinned" class="pin-text flex-grow-1">Pinned by you</div>
                </div>
                <!--  -->
                <div class="d-flex align-items-start">
                    <div class="me-3">
                        <img :src="message.profileImg" alt="Profile Photo">
                    </div>
                    <div>
                    <div class="d-flex items-align-center mb-2">
                        <div class="fs-6 fw-bold me-2">{{message.sender}}</div>
                        <div class="pin-time-box">{{message.time}}</div>
                    </div>
                    <div class="mb-3">
                        {{message.content}}
                    </div>
                    </div>
                </div>
                <!-- Pin message  -->
                <div>
                    <div v-if="message.pinned == false" class="mb-3">
                        <button class="px-2" @click="pinMessage(message)">Pin message</button>
                    </div>
                    <div v-else class="mb-3">
                        <button @click="toggleModal">Unpin message</button>
                    </div>
                </div>
                <!--  -->
            </div>
        </div>

        
        <!-- Modal Component. To take props -->
        <div id="modal-wrapper" class="modal-wrapper">
            <div class="modal-block bg-white px-4 py-4">
                <div class="d-flex justify-content-between align-items-center mb-3">
                <h2 class="modal-title fs-3 fw-bold">Remove Pinned Item</h2>
                <h2 @click="toggleModal" class="mb-0">X</h2>
                </div>
                <div class="modal-title__text fw-bold mb-4">
                Are you sure you want to remove this pinned item?
                </div>
                <div class="modal-box border-1 rounded-3 mb-5 px-3 py-4">
                <div class="d-flex align-items-center mb-2">
                    <div class="me-2">
                    <img
                        class="rounded-circle"
                        src="../assets/profile-photo.png"
                        alt="Profile photo"
                    />
                    </div>
                    <div class="modal-box-title fw-bold">Deyrin Cutting</div>
                </div>
                <div class="modal-box-text mb-2">
                    Wow! Thank you. It's working! I spent many hours on this case,
                    completely paying no attention to the css scope Thanks for that.
                </div>
                <div class="modal-box-time">Today at 12:34am</div>
                </div>
                <div class="d-flex justify-content-end">
                <button
                    @click="toggleModal"
                    class="modal-btn-1 py-3 me-3 rounded-2 border-1 fw-bold"
                >
                    Cancel
                </button>
                <button
                    @click="unpinMessage(message)"
                    id="close-btn"
                    class="
                    modal-btn
                    py-3
                    rounded-2
                    border-0
                    bg-success
                    text-white
                    fw-normal
                    "
                >
                    Remove Pinned Item
                </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "PinMessage2",
  data() {
    return {
      counter: 0,
      pinned: false,
      messageList: [
        {
          sender: "blac_dev",
          profileImg: require("../assets/profile-photo.png"),
          time: "7:27pm",
          content: "Wow! Thank you. It's working! I spent many hours on this case,completely paying no attention to the css scope Thanks for that.",
          pinned: false,
        },
        {
          sender: "Fae",
          profileImg: require("../assets/profile-photo.png"),
          time: "2:23pm",
          content: "Bro, where you at, come online asap!",
          pinned: false,
        },
        {
          sender: "Delight",
          profileImg: require("../assets/profile-photo.png"),
          time: "2:23pm",
          content: "I'm at your place",
          pinned: false,
        },
      ]
    };
  },
  methods: {
    pinMessage: function (message) {
        message.pinned = true;
        this.counter++;
    },
    unpinMessage: function (message) {
      this.$emit(message.pinned = false);
      this.counter--;
      this.toggleModal();
    },
    toggleModal: function () {
      const modalBox = document.getElementById("modal-wrapper");
      modalBox.classList.toggle("toggleModal");
    },
  },
};
</script>

<style scoped>
/* Modal */
.modal-wrapper {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.3);
  display: none;
}
.modal-block {
  max-width: 650px;
}
.modal-title {
  color: #1d1d1d;
}
.modal-title__text {
  color: #999999;
}
.modal-box {
  border: 1px solid #999999;
}
.modal-box-title {
  color: #242424;
}
.modal-box-text {
  color: #616061;
}
.modal-box-time {
  color: #999999;
}
.modal-btn {
  width: 175px;
}
.modal-btn-1 {
  width: 175px;
  border: 1px solid #999999;
  color: #616061;
}
.toggleModal {
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Media queries */
@media screen and (max-width: 475px) {
  .modal-block {
    font-size: 12px;
  }
  .modal-btn, .modal-btn-1 {
    font-size: 12px;
    width: 100px;
  }
}

/* Pin Message */
.pinned-info {
  background-color: #E1FDF4;
}
.pin-block {
  background-color: #E1FDF4;
  font-size: 15px;
}
.pin-text {
  font-size: 14px;
  color: #999999;
}
.pin-image-box {
  min-width: 36px;
}
.pin-time-box {
  min-width: 55px;
  color: #616061;
}
</style>
