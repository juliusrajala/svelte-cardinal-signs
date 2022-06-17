<div>
  <span />
  <span />
</div>

<style>
  div {
    display: flex;
    flex-direction: column;
    width: 50px;
    height: 400px;
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
  }

  span {
    flex: 1;
  }

  span:nth-child(2) {
    background-color: #000;
  }

  span:nth-child(1) {
    background-color: #ff0;
  }
</style>
