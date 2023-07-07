<script setup>
import { ref, reactive, computed, watch, onMounted } from 'vue';

const showPreviewAndSource = ref(false);

const form = reactive({
  'color': null,
  'avatar': null,
  'fullname': null,
  'logo': null,
  'jobtitle': null,
  'department': null,
  'company': null,
  'phone': null,
  'mobile': null,
  'email': null,
  'website': null,
  'addressline1': null,
  'addressline2': null,
  'addressline3': null,
  'zipcode': null,
  'locality': null,
  'country': null,
  'facebook': null,
  'twitter': null,
  'linkedin': null,
  'instagram': null,
  'youtube': null,
  'bannerimg': null,
  'bannerurl': null,
  'ecofriendly': null,
  'privacy': null,
});

const color = computed(() => {
  if (!form.color) return '#f000b8';
  return ((new RegExp('^#(?:[0-9a-f]{3}){1,2}$')).test(form.color.toLowerCase())) ? form.color : '#f000b8';
});

const html = computed(() => {

  let avatar = '';
  if (form.avatar) {
    avatar = `
      <tr>
        <td style="text-align: center;">
          <img src="${form.avatar}" alt="Avatar" width="140"
            style="display: block; max-width: 140px;">
        </td>
      </tr>
      <tr>
        <td height="20"></td>
      </tr>
    `;
  }

  let logo = '';
  if (form.logo) {
    logo = `
      <tr>
        <td style="text-align: center;">
          <img src="${form.logo}" alt="Logo" width="140" style="display: block; max-width: 140px;">
        </td>
      </tr>
      <tr>
        <td height="20"></td>
      </tr>
    `;
  }

  let facebook = '';
  if (form.facebook) {
    facebook = `
      <td>
        <a href="${form.facebook}" color="${color.value}"
          style="display: inline-block; padding: 0px; background-color: ${color.value}">
          <img
            src="https://cdn2.hubspot.net/hubfs/53/tools/email-signature-generator/icons/facebook-icon-2x.png"
            alt="facebook" color="${color.value}" height="24"
            style="max-width: 135px; display: block; background-color: ${color.value}">
        </a>
      </td>
      <td width="5">
        <div></div>
      </td>
    `;
  }

  let twitter = '';
  if (form.twitter) {
    twitter = `
      <td>
        <a href="${form.twitter}" color="${color.value}"
          style="display: inline-block; padding: 0px; background-color: ${color.value}">
          <img
            src="https://cdn2.hubspot.net/hubfs/53/tools/email-signature-generator/icons/twitter-icon-2x.png"
            alt="twitter" color="${color.value}" height="24"
            style="max-width: 135px; display: block; background-color: ${color.value}">
        </a>
      </td>
      <td width="5">
        <div></div>
      </td>
    `;
  }

  let linkedin = '';
  if (form.linkedin) {
    linkedin = `
      <td>
        <a href="${form.linkedin}" color="${color.value}"
          style="display: inline-block; padding: 0px; background-color: ${color.value}">
          <img
            src="https://cdn2.hubspot.net/hubfs/53/tools/email-signature-generator/icons/linkedin-icon-2x.png"
            alt="linkedin" color="${color.value}" height="24"
            style="max-width: 135px; display: block; background-color: ${color.value}">
        </a>
      </td>
      <td width="5">
        <div></div>
      </td>
    `;
  }

  let instagram = '';
  if (form.instagram) {
    instagram = `
      <td>
        <a href="${form.instagram}" color="${color.value}"
          style="display: inline-block; padding: 0px; background-color: ${color.value}">
          <img
            src="https://cdn2.hubspot.net/hubfs/53/tools/email-signature-generator/icons/instagram-icon-2x.png"
            alt="instagram" color="${color.value}" height="24"
            style="max-width: 135px; display: block; background-color: ${color.value}">
        </a>
      </td>
      <td width="5">
        <div></div>
      </td>
    `;
  }

  let youtube = '';
  if (form.youtube) {
    youtube = `
      <td>
        <a href="${form.youtube}" color="${color.value}"
          style="display: inline-block; padding: 0px; background-color: ${color.value}">
          <img
            src="https://cdn2.hubspot.net/hubfs/53/tools/email-signature-generator/icons/instagram-icon-2x.png"
            alt="YouTube" color="${color.value}" height="24"
            style="max-width: 135px; display: block; background-color: ${color.value}">
        </a>
      </td>
    `;
  }

  let fullname = '';
  if (form.fullname) {
    fullname = `
      <h2 color="#000000" style="margin: 0px; font-size: 18px; color: rgb(0, 0, 0); font-weight: 600;">
        <span>${form.fullname}</span>
      </h2>
    `;
  }

  let jobtitle = '';
  if (form.jobtitle) {
    jobtitle = `
      <p color="#000000" font-size="medium"
        style="margin: 0px; color: rgb(0, 0, 0); font-size: 14px; line-height: 22px;">
        <span>${form.jobtitle}</span>
      </p>
    `;
  }

  let departmentCompany = '';
  if (form.department && form.company) {
    departmentCompany = `
      <p color="#000000" font-size="medium"
        style="margin: 0px; font-weight: 500; color: rgb(0, 0, 0); font-size: 14px; line-height: 22px;">
        <span>${form.department}</span>
        <span>&nbsp;|&nbsp;</span>
        <span>${form.company}</span>
      </p>
    `;
  } else if (form.department) {
    departmentCompany = `
      <p color="#000000" font-size="medium"
        style="margin: 0px; font-weight: 500; color: rgb(0, 0, 0); font-size: 14px; line-height: 22px;">
        <span>${form.department}</span>
      </p>
    `;
  } else if (form.company) {
    departmentCompany = `
      <p color="#000000" font-size="medium"
        style="margin: 0px; font-weight: 500; color: rgb(0, 0, 0); font-size: 14px; line-height: 22px;">
        <span>${form.company}</span>
      </p>
    `;
  }

  let phone = '';
  if (form.phone) {
    phone = `
      <tr height="25" style="vertical-align: middle;">
        <td width="24" style="vertical-align: middle;">
          <table cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
            <tbody>
              <tr>
                <td style="vertical-align: bottom;">
                  <img src="/img/phone.png" color="${color.value}" alt="phone" width="16" height="16"
                    style="display: block;">
                </td>
              </tr>
            </tbody>
          </table>
        </td>
        <td style="padding: 0px; color: rgb(0, 0, 0);">
          <a href="tel:${form.phone}" color="#000000"
            style="text-decoration: none; color: rgb(0, 0, 0); font-size: 12px;">
            <span>${form.phone}</span>
          </a>
        </td>
      </tr>
    `;
  }

  let mobile = '';
  if (form.mobile) {
    mobile = `
      <tr height="25" style="vertical-align: middle;">
        <td width="24" style="vertical-align: middle;">
          <table cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
            <tbody>
              <tr>
                <td style="vertical-align: bottom;">
                  <img src="/img/mobile.png" color="${color.value}" alt="mobile" width="16" height="16"
                    style="display: block;">
                </td>
              </tr>
            </tbody>
          </table>
        </td>
        <td style="padding: 0px; color: rgb(0, 0, 0);">
          <a href="tel:${form.mobile}" color="#000000"
            style="text-decoration: none; color: rgb(0, 0, 0); font-size: 12px;">
            <span>${form.mobile}</span>
          </a>
        </td>
      </tr>
    `;
  }

  let email = '';
  if (form.email) {
    email = `
     <tr height="25" style="vertical-align: middle;">
        <td width="24" style="vertical-align: middle;">
          <table cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
            <tbody>
              <tr>
                <td style="vertical-align: bottom;">
                  <img src="/img/email.png" color="${color.value}" alt="email" width="16" height="16"
                    style="display: block;">
                </td>
              </tr>
            </tbody>
          </table>
        </td>
        <td style="padding: 0px;">
          <a href="mailto:${form.email}" color="#000000"
            style="text-decoration: none; color: rgb(0, 0, 0); font-size: 12px;">
            <span>${form.email}</span>
          </a>
        </td>
      </tr>
    `;
  }

  let website = '';
  if (form.website) {
    website = `
      <tr height="25" style="vertical-align: middle;">
        <td width="24" style="vertical-align: middle;">
          <table cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
            <tbody>
              <tr>
                <td style="vertical-align: bottom;">
                  <img src="/img/website.png" color="${color.value}" alt="website" width="16" height="16"
                    style="display: block;">
                </td>
              </tr>
            </tbody>
          </table>
        </td>
        <td style="padding: 0px;">
          <a href="${form.website}" color="#000000"
            style="text-decoration: none; color: rgb(0, 0, 0); font-size: 12px;">
            <span>${form.website}</span>
          </a>
        </td>
      </tr>
    `;
  }

  let address = '';
  if (form.addressline1 || form.addressline2 || form.addressline3 || form.zipcode || form.locality || form.country) {

    let lines = [];

    if (form.addressline1) {
      lines.push(form.addressline1);
    }

    if (form.addressline2) {
      lines.push(form.addressline2);
    }

    if (form.addressline3) {
      lines.push(form.addressline3);
    }

    let line4 = [];
    if (form.zipcode && form.locality) {
      line4.push(`${form.zipcode} ${form.locality}`)
    } else if (form.zipcode) {
      line4.push(form.zipcode);
    } else if (form.locality) {
      line4.push(form.locality);
    }

    if (form.country) {
      line4.push(form.country);
    }

    if (line4) {
      lines.push(line4.join(', '))
    }

    address = `
      <tr height="25" style="vertical-align: top;">
        <td width="24" style="vertical-align: top;">
          <table cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
            <tbody>
              <tr>
                <td style="vertical-align: bottom;">
                  <img src="/img/address.png" color="${color.value}" alt="address" width="16" height="16"
                    style="display: block;">
                </td>
              </tr>
            </tbody>
          </table>
        </td>
        <td style="padding: 0px;">
          <span color="#000000" style="font-size: 12px; color: rgb(0, 0, 0);">
            <span>${lines.join('<br>')}</span>
          </span>
        </td>
      </tr>
    `;
  }

  let banner = '';
  if (form.bannerimg && form.bannerurl) {
    banner = `
      <tr>
        <td>
          <table cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
            <tbody>
              <tr>
                <td height="20"></td>
              </tr>
              <tr>
                <span style="display: block; text-align: left;">
                  <a target="_blank" rel="noopener noreferrer" href="${form.bannerurl}"
                    style="border-width: initial; border-style: none; border-color: initial; display: inline-block; background-color: transparent; color: rgb(255, 255, 255); font-weight: 700; text-decoration: none; text-align: center; line-height: 1; font-size: 12px; border-radius: 3px;">
                    <img src="${form.bannerimg}" alt="Bannière" style="text-decoration: none; max-width:400px;">
                  </a>
                </span>
              </tr>
            </tbody>
          </table>
        </td>
      </tr>
    `;
  } else if (form.bannerimg) {
    banner = `
      <tr>
        <td>
          <table cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
            <tbody>
              <tr>
                <td height="20"></td>
              </tr>
              <tr>
                <span style="display: block; text-align: left;">
                  <img src="${form.bannerimg}" alt="Bannière" style="text-decoration: none; max-width: 400px;">
                </span>
              </tr>
            </tbody>
          </table>
        </td>
      </tr>
    `;
  }

  let ecofriendly = '';
  if (form.ecofriendly) {
    ecofriendly = `
      <tr v-if="form.ecofriendly">
        <td>
          <table width="600" cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: small; font-family: Arial;">
            <tbody>
              <tr>
                <td height="20"></td>
              </tr>
              <tr height="25" style="vertical-align: top;">
                <td width="20" style="vertical-align: top;">
                  <table cellpadding="0" cellspacing="0"
                    style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
                    <tbody>
                      <tr>
                        <td style="vertical-align: bottom;">
                          <span color="${color.value}" width="14" style="display: inline-block; background-color: ${color.value}">
                            <img
                              src="https://cdn2.hubspot.net/hubfs/53/tools/email-signature-generator/icons/address-icon-2x.png"
                              color="${color.value}" alt="Eco" width="14" style="display: block; background-color: ${color.value}">
                          </span>
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </td>
                <td style="padding: 0px;">
                  <span color="#27ae60" style="font-size: 12px; line-height: 16px; color: #27ae60;">
                    <span>${form.ecofriendly}</span>
                  </span>
                </td>
              </tr>
            </tbody>
          </table>
        </td>
      </tr>
    `;
  }

  let privacy = '';
  if (form.privacy) {
    privacy = `
      <tr v-if="form.privacy">
        <td>
          <table width="600" cellpadding="0" cellspacing="0"
            style="vertical-align: -webkit-baseline-middle; font-size: small; font-family: Arial;">
            <tbody>
              <tr>
                <td height="20"></td>
              </tr>
              <tr height="25" style="vertical-align: top;">
                <td style="padding: 0px;">
                  <span color="#999" style="font-size: 12px; line-height: 16px; color: #999;">
                    <span>${form.privacy}</span>
                  </span>
                </td>
              </tr>
            </tbody>
          </table>
        </td>
      </tr>
    `;
  }


  return `
    <table cellpadding="0" cellspacing="0" style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
      <tbody>
        <tr>
          <td>
            <table cellpadding="0" cellspacing="0"
              style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
              <tbody>
                <tr>
                  <td style="vertical-align: top;">
                    <table cellpadding="0" cellspacing="0"
                      style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
                      <tbody>
                        ${avatar}
                        ${logo}
                        <tr>
                          <td style="text-align: center;">
                            <table cellpadding="0" cellspacing="0"
                              style="display: inline-block; vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
                              <tbody>
                                <tr style="text-align: center;">
                                  ${facebook}
                                  ${twitter}
                                  ${linkedin}
                                  ${instagram}
                                  ${youtube}
                                </tr>
                              </tbody>
                            </table>
                          </td>
                        </tr>
                      </tbody>
                    </table>
                  </td>
                  <td width="30">
                    <div></div>
                  </td>
                  <td style="padding: 0px; vertical-align: middle;">
                    ${fullname}
                    ${jobtitle}
                    ${departmentCompany}
                    <table cellpadding="0" cellspacing="0"
                      style="width: 100%; vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
                      <tbody>
                        <tr>
                          <td height="20"></td>
                        </tr>
                      </tbody>
                    </table>
                    <table cellpadding="0" cellspacing="0"
                      style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
                      <tbody>
                        ${phone}
                        ${mobile}
                        ${email}
                        ${website}
                        ${address}
                      </tbody>
                    </table>
                    <table cellpadding="0" cellspacing="0"
                      style="vertical-align: -webkit-baseline-middle; font-size: medium; font-family: Arial;">
                      <tbody>
                        <tr>
                          <td height="20"></td>
                        </tr>
                      </tbody>
                    </table>
                  </td>
                </tr>
              </tbody>
            </table>
          </td>
        </tr>
        ${banner}
        ${ecofriendly}
        ${privacy}
      </tbody>
    </table>
  `
});

const htmlClean = computed(() => {
  return html.value
    .replace(/\>[\r\n ]+\</g, "><")
    .replace(/(<.*?>)|\s+/g, (m, $1) => $1 ? $1 : ' ')
    .trim();
});

watch(form, () => {
  checkShowPreviewAndSource();
});

onMounted(() => {
  checkShowPreviewAndSource();
});

function checkShowPreviewAndSource() {
  showPreviewAndSource.value = false;
  for (const [k, v] of Object.entries(form)) {
    if (v) {
      showPreviewAndSource.value = true;
    }
  }
};

</script>

<template>
  <div class="container mx-auto flex gap-6 my-6 px-4">
    <div class="flex-1 bg-base-200 rounded-lg p-4">
      <div>

        <h1 class="text-2xl font-semibold text-primary">Générateur de signatures</h1>

        <form autocomplete="off">
          <div class="form-control">
            <label class="label" for="color">
              <span class="label-text">Couleur</span>
            </label>
            <div class="flex gap-2">
              <input type="text" id="color" class="input input-bordered w-full" v-model="form.color" />
              <div class="aspect-square h-12 rounded-lg" :style="{ backgroundColor: color }"></div>
            </div>

          </div>
          <div class="form-control">
            <label class="label" for="avatar">
              <span class="label-text">Avatar</span>
              <span class="label-text-alt">140&times;140px</span>
            </label>
            <input type="url" id="avatar" class="input input-bordered" v-model="form.avatar" />
          </div>
          <div class="form-control">
            <label class="label" for="fullname">
              <span class="label-text">Prénom et nom</span>
            </label>
            <input type="text" id="fullname" class="input input-bordered" v-model="form.fullname" />
          </div>
          <div class="form-control">
            <label class="label" for="logo">
              <span class="label-text">Logo</span>
            </label>
            <input type="url" id="logo" class="input input-bordered" v-model="form.logo" />
          </div>
          <div class="form-control">
            <label class="label" for="jobtitle">
              <span class="label-text">Titre ou poste</span>
            </label>
            <input type="text" id="jobtitle" class="input input-bordered" v-model="form.jobtitle" />
          </div>
          <div class="form-control">
            <label class="label" for="department">
              <span class="label-text">Service</span>
            </label>
            <input type="text" id="department" class="input input-bordered" v-model="form.department" />
          </div>
          <div class="form-control">
            <label class="label" for="company">
              <span class="label-text">Entreprise</span>
            </label>
            <input type="text" id="company" class="input input-bordered" v-model="form.company" />
          </div>
          <div class="form-control">
            <label class="label" for="phone">
              <span class="label-text">Téléphone</span>
            </label>
            <input type="text" id="phone" class="input input-bordered" v-model="form.phone" />
          </div>
          <div class="form-control">
            <label class="label" for="mobile">
              <span class="label-text">Mobile</span>
            </label>
            <input type="text" id="mobile" class="input input-bordered" v-model="form.mobile" />
          </div>
          <div class="form-control">
            <label class="label" for="email">
              <span class="label-text">Adresse e-mail</span>
            </label>
            <input type="email" id="email" class="input input-bordered" v-model="form.email" />
          </div>
          <div class="form-control">
            <label class="label" for="website">
              <span class="label-text">Site internet</span>
            </label>
            <input type="url" id="website" class="input input-bordered" v-model="form.website" />
          </div>
          <div class="form-control">
            <label class="label" for="address">
              <span class="label-text">Adresse</span>
            </label>
            <input type="text" placeholder="Ligne 1" id="address" class="input input-bordered"
              v-model="form.addressline1" />
            <input type="text" placeholder="Ligne 2" class="input input-bordered mt-2" v-model="form.addressline2" />
            <input type="text" placeholder="Ligne 3" class="input input-bordered mt-2" v-model="form.addressline3" />
            <input type="text" placeholder="Code postal" class="input input-bordered mt-2" v-model="form.zipcode" />
            <input type="text" placeholder="Ville" class="input input-bordered mt-2" v-model="form.locality" />
            <input type="text" placeholder="Pays" class="input input-bordered mt-2" v-model="form.country" />
          </div>
          <div class="form-control">
            <label class="label" for="facebook">
              <span class="label-text">Facebook</span>
            </label>
            <input type="url" id="facebook" class="input input-bordered" v-model="form.facebook" />
          </div>
          <div class="form-control">
            <label class="label" for="twitter">
              <span class="label-text">Twitter</span>
            </label>
            <input type="url" id="twitter" class="input input-bordered" v-model="form.twitter" />
          </div>
          <div class="form-control">
            <label class="label" for="linkedin">
              <span class="label-text">LinkedIn</span>
            </label>
            <input type="url" id="linkedin" class="input input-bordered" v-model="form.linkedin" />
          </div>
          <div class="form-control">
            <label class="label" for="instagram">
              <span class="label-text">Instagram</span>
            </label>
            <input type="url" id="instagram" class="input input-bordered" v-model="form.instagram" />
          </div>
          <div class="form-control">
            <label class="label" for="youtube">
              <span class="label-text">YouTube</span>
            </label>
            <input type="url" id="youtube" class="input input-bordered" v-model="form.youtube" />
          </div>
          <div class="form-control">
            <label class="label" for="bannerimg">
              <span class="label-text">Image de la bannière</span>
              <span class="label-text-alt">400&times;100px</span>
            </label>
            <input type="url" id="bannerimg" class="input input-bordered" v-model="form.bannerimg" />
          </div>
          <div class="form-control">
            <label class="label" for="bannerurl">
              <span class="label-text">Lien sur la bannière</span>
            </label>
            <input type="url" id="bannerurl" class="input input-bordered" v-model="form.bannerurl" />
          </div>
          <div class="form-control">
            <label class="label" for="ecofriendly">
              <span class="label-text">Éco-responsabilité</span>
            </label>
            <textarea id="ecofriendly" class="textarea textarea-bordered" rows="6" v-model="form.ecofriendly"></textarea>
          </div>
          <div class="form-control">
            <label class="label" for="privacy">
              <span class="label-text">Avis de confidentialité</span>
            </label>
            <textarea id="privacy" class="textarea textarea-bordered" rows="6" v-model="form.privacy"></textarea>
          </div>
        </form>

      </div>
    </div>
    <div id="preview" class="flex-shrink-0">
      <div class="sticky top-6" v-if="showPreviewAndSource">
        <div v-html="html" class="mb-6"></div>
        <textarea class="textarea textarea-bordered w-full" v-html="htmlClean" rows="15"></textarea>
      </div>
    </div>
  </div>
</template>

<style scoped>
#preview {
  width: 600px;
}

input:invalid {
  @apply input-error;
}
</style>
