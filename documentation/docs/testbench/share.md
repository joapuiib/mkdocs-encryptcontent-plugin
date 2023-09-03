title: Encode share link

#Various tests

[Test1 (user: dave)](userpass1.md#P2RhdmU6b3hpZGl6ZQ)

[Test2 (user: dave, go to anchor-6)](anchor.md#P2RhdmU6b3hpZGl6ZQ#anchor-6)

[Test3 (password: squirrel)](onlypasswords2.md#PzpzcXVpcnJlbA)

[Test4 (obfuscate: Crawler be gone!)](obfuscate.md#PzpDcmF3bGVyJTIwYmUlMjBnb25lIQ)

# Create share link

<div class="w3-row-padding" style="padding-left: 0px;">
  <div class="w3-third">
    <label for="share-user">User</label>
    <input class="w3-input w3-border w3-hover-theme w3-theme-l1" name="share-user" id="share-user" type="text" value="dave" onchange="genB64Url();">
  </div>
  <div class="w3-third">
    <label for="share-pass">Password</label>
    <input class="w3-input w3-border w3-hover-theme w3-theme-l1" name="share-pass" id="share-pass" type="text" value="oxidize" onchange="genB64Url();">
  </div>
</div>

<div class="w3-row-padding w3-margin-top" style="padding-left: 0px;">
  <div class="w3-twothird">
    <label for="share-output">Output</label>
    <code name="share-output" id="share-output" type="text"></code>
    <div id="output-length"></div>
  </div>
</div>

<div class="w3-row-padding w3-margin-top" style="padding-left: 0px;">
  <div class="w3-twothird">
    <label for="share-decode">Decoded</label>
    <code name="share-decode" id="share-decode" type="text"></code>
    <div id="decode-length"></div>
  </div>
</div>

<script>
var share_user = document.getElementById('share-user');
var share_pass = document.getElementById('share-pass');
var share_output = document.getElementById('share-output');
var share_decode = document.getElementById('share-decode');
var output_length = document.getElementById('output-length');
var decode_length = document.getElementById('decode-length');


function base64url_decode(input) {
    return atob(input.replace(/-/g, '+').replace(/_/g, '/'))
}
function base64url_encode(input) {
    return btoa(input).replace(/\+/g, '-').replace(/\//g, '_').replace(/=+$/, '');
}


function genB64Url() {
    const str = "?" + encodeURIComponent(share_user.value) + ":" + encodeURIComponent(share_pass.value);
    let encstr = base64url_encode(str);
    share_output.textContent = '#' + encstr;
    output_length.innerHTML = "Length: " + encstr.length;
    let decstr = base64url_decode(encstr)
    share_decode.textContent = decstr;
    decode_length.innerHTML = "Length: " + decstr.length;
}
genB64Url();

</script>