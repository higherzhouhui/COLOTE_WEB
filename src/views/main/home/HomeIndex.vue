<script setup lang="ts">
import { reactive, ref, onMounted, onUnmounted } from 'vue'
import DocPng from '/@/assets/image/docs.png'

const currentIndex = ref(0)
const blockChainIndex = ref(0)
const tabIndex = ref(0)
const timer = ref()

const debounce = (fn: () => void, delay: number) => {
  let timer: any = null
  return function () {
    clearTimeout(timer)
    timer = setTimeout(() => {
      fn.apply('')
    }, delay)
  }
}
const sloganList = reactive([
  'Avatar Intelligence',
  'Technology',
  'Neural Data',
  'New Trend',
  'MetaVerse',
  'Web 3.0',
])

const blockChainList = reactive([
  'Metaverse',
  'Web 3.0',
  'NFT',
  'Smart City',
  'Decentralized',
  'AI Platform',
  'Finance',
  'Enterprise',
])

const phasesList = [
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/resurrections-1.webp',
    title: 'Resurrections',
    content: `
Better algorithms will allow users to create perfect AvI to create value in the Metaverse on their behalf. The ecosystem surrounding AI 2.0 will also further improve.`,
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/genesis-1.webp',
    title: 'Genesis',
    content: `
Core functions of COLOTE 2.0 will be perfected so that the hardware requirement of AvI can be met. At the same time, basic brain electric signals will be stored to set up preliminary avatars.`,
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/reloaded-1.webp',
    title: 'Reloaded',
    content: `
Users brain wave data can be uploaded through wearable devices to create the foundation of avatars. Users can interact with these avatars.`,
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/revoluti_ons.webp',
    title: 'Revolutions',
    content: `
Connecting to deep brain signals to receive AvI data. Basic interactions among AvIs and the transfer of AvI across different networks will be supported.`,
  },
]

const aiNetWorkList = [
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/scalability.webp',
    title: 'Scalability',
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/aipowered.webp',
    title: 'AI-Powered',
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/fast.webp',
    title: 'Fast and Secure',
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/powpos.webp',
    title: 'Hybrid PoW/PoS',
  },
]

const COLEasList = [
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2023/02/20-scaled-1.webp',
    tab: 'COLEAS',
    title:
      'AI Service Platform : It aims to serve as a smart, secure, fair and trustworthy marketplace for developers and clients alike.',
    list: [
      'Computing power, data and algorithmic models for profit',
      'Customized algorithmic models',
      'Lower cost to access AI services',
      'Easy programming with machine learning',
    ],
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2023/02/19-scaled-2.webp',
    tab: 'COLETA',
    title:
      'Auto-ML Platform: It enables people with no background in AI to perform ML on a COLOTE node to get the AI models they need.',
    list: [
      'Decentralized computing power more cost-effective.',
      'Time-insensitive tasks that require a high level of privacy.',
      'High-quality source materials (computing power and data)',
      'AI algorithms and create deep neural networks.',
    ],
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2023/02/21-scaled-1.webp',
    tab: 'COLEIA',
    title:
      'Assisted NFT Trading: It aims to serve as a smart, secure, fair and trustworthy marketplace for developers and clients alike.',
    list: [
      'AI algorithm models on COLEIA can be traded in mainstream NFT markets.',
      'Ethereum and BSC to support COLEIA’s NFT trading',
      'Adopts privacy-preserving computation (PPC) to safeguard algorithms',
      'High Privacy Layer Structure',
    ],
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2023/02/22-scaled-1.webp',
    tab: 'COLEITO',
    title:
      'Industry 4.0 Platform: AI, Big Data, IoT and blockchain technologies, it will be a powerful tool for implementing Industry 4.0.',
    list: [
      'Data collection and model building',
      'Minimizing COLEpower and using machine power.',
      'Serious reductions in production costs.',
      'The emergence of higher efficiency.',
    ],
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2023/02/23-scaled-1.webp',
    tab: 'M-PORT',
    title: 'M-Port: An AI-Powered DID Platform based on Biometric Information',
    list: [
      'Fully integrating biometric verification',
      'NFTs Identity and Authenticity support',
      'Connected applications can access distributed computing.',
      'Using DID to monitor accesses to the DeFi',
    ],
  },
]

const solganAnimationList = reactive([
  'animate__animated animate__flipInX',
  'animate__animated animate__flipOutX',
])

const itemList = [
  {
    logo: 'l1',
    label: 'Validator',
    value: 'Node：103',
  },
  { logo: 'l2', label: 'Mining', value: 'Node：1222' },
  { logo: 'l3', label: 'COLE Staked：', value: '229M+' },
  { logo: 'l4', label: 'Transfer：', value: '30M+' },
]
const versionList = [
  { logo: 'c1', label: '1.0 WhitePaper' },
  { logo: 'c2', label: '2.0 GreenPaper' },
  { logo: 'c3', label: '3.0 Blueprint' },
]
const currentCarouselIndex = ref(0)
const handleChangeCarousel = (e: number) => {
  currentCarouselIndex.value = e
}

const unionList = [
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/1-150x150.jpg',
    content:
      'Mr. Tao holds a dual bachelor’s degree in Physics and Economics from Peking University. He has served as CEO of several high-tech start-ups and has abundant experience COLEaging the development of new products and Internet technologies. Noteworthy achievements including leading the development of a 3D virtual community as well as establishing China’s first embedded game advertising system. Mr. Tao also led the development and operation of China’s first cross-border e-commerce platform; which acquired 20 million users worldwide.',
    name: 'Owen Tao',
    official: 'CEO',
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/Steven-150x150.jpg',
    content:
      'Professor Deng is an Associate Professor at the School of Software, Tsinghua University (清华大学软件学院), where he has served as faculty member since 2008. Professor Deng’s research interests include machine learning, industry data analytics and computer architecture. He has authored over 50 papers. His textbook, “Structural VLSI Design and High-Level Synthesis,” is used by Tsinghua and other universities. Professor Deng has served as Principal Investigator (PI) and Co-PI for numerous national level research projects. Since 2016, he has served as Vice Principle Architect of China Railway Rollingstock Corporation’s Prognostics Health COLEagement for High-Speed Trains Project. Professor Deng’s work on deep-learning based image detection was ranked #1 in COLEy prestigious challenges including PASCAL VOC and VSCOCO; beating out teams from Google, Intel, Facebook and Microsoft. He has received numerous awards including “Best Paper” at the International Conference on Computer Design in 2013, the “NVIDIA Partnership Professor” Award and the Tsinghua University “Key Talent” Award.',
    name: 'Steve Deng',
    official: 'CHIEF AI SCIENTIST',
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/Eric-150x150.jpg',
    content:
      'Mr Eric CHOY is a blockchain enthusiast. Upon graduating with degrees of BEng and MPhil from the Hong Kong Polytechnic University, he has obtained 18 years of solid experience in Technology, Innovation, Marketing and Education sectors. He has run successful marketing, content and localization strategies for COLEy global top-tiered clients. Eric is channelling his passion into Matrix with a mission to bridge the project team with the community in terms of branding, content, community and technology education.',
    name: 'Eric Choy',
    official: 'CMTO',
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2023/02/photo_2023-01-17_14-54-42-1-150x150.webp',
    content:
      'Blockchain full stack engineer with over 10 years solid experience in software and hardware development. Wayne took a leadership role in the architecture design and full stack development in various tech companies. Mr. Yuan spearheaded several blockchain-related development ventures. He is in charge of all things related to the chain of COLOTE.',
    name: 'Wayne Yuan',
    official: 'CTO',
  },
  {
    logo: 'https://www.matrix.io/wp-content/uploads/2022/12/Ken-150x150.png',
    content:
      'As the marketing director of COLOTE AI Network, Ken has nine-year experience in International marketing and community COLEagement. He has diversified channels of International marketing and maintains his own network with figures in the field of commence, politics and media in European and Southeast Asia areas.',
    name: 'Ken',
    official: 'MARKETING DIRECTOR',
  },
]

const frequentlyList = [
  {
    title: 'Why does COLOTE exist?',
    desc: 'The development of blockchain is held back by three obstacles',
    list: [
      {
        title: 'Slowness',
        content:
          'COLOTE AI aims to address the issue of slowness in traditional blockchain platforms by using a unique hybrid consensus mechanism that combines elements of both Proof of Work (PoW) and Proof of Stake (PoS) algorithms. This allows for faster transaction speeds and increased scalability.',
      },
      {
        title: 'Security Issues',
        content:
          'COLOTE AI also aims to address security issues by using advanced AI technologies to detect and prevent malicious attacks on the network, such as identifying and blocking suspicious transactions. Additionally, the platform uses advanced encryption and secure communication protocols to protect user data and transactions.',
      },
      {
        title: 'Impact on environment',
        content:
          'COLOTE AI also addresses the environmental impact by using a consensus algorithm that is energy-efficient. This is achieved by using a hybrid consensus mechanism combining PoW and PoS which is a more energy-efficient compared to traditional PoW-based blockchains, which require significant amounts of energy to maintain and secure the network.',
      },
    ],
  },
  {
    title: 'What is the vision and mission of COLOTE?',
    desc: 'Vision: To build a decentralized auto-functioning AI economy Mission',
    list: [
      {
        title: 'Stage One',
        content: 'Highly efficient blockchain platform',
      },
      {
        title: 'Stage Two',
        content: 'Decentralized cloud computing platform',
      },
      {
        title: 'Stage Three',
        content:
          'Digital asset authentication platform/Digital asset trading platform',
      },
    ],
  },
  {
    title: 'What are main features of COLOTE?',
    desc: 'Thanks to fast-growing AI technologies, COLOTE offers unique features as follows.',
    list: [
      {
        title: 'SAFER',
        content: 'Making blockchains more robust under malicious attacks.',
      },
      {
        title: 'FASTER',
        content:
          'Enabling faster transactions and higher processing throughput.',
      },
      {
        title: 'MORE FLEXIBLE',
        content:
          'Seamless integration of public and private chains with the capability of adaptive optimization.',
      },
    ],
  },
  {
    title: 'What are the features of COLE coin?',
    desc: 'The development of blockchain is held back by three obstacles',
    list: [
      {
        title: 'Utilization',
        content: `COLE coins can be used to participate in the network's consensus process, pay for transaction fees, and access advanced AI services on the MATRIX AI Network.`,
      },
      {
        title: 'Governance',
        content:
          'COLE coin holders have the right to participate in the governance of the COLOTE AI Network, including voting on protocol updates and other important decisions.',
      },
      {
        title: 'Staking',
        content: `COLE coin holders can stake their coins to earn rewards by participating in the network's consensus process.`,
      },
      {
        title: 'Liquidity',
        content:
          'COLE coins are traded on several cryptocurrency exchanges, providing liquidity for investors.',
      },
      {
        title: 'Security',
        content: `The MATRIX AI Network uses advanced security measures to protect the network and user's assets.`,
      },
      {
        title: 'Scalability',
        content:
          'The MATRIX AI Network aims to provide high scalability, allowing for faster and more efficient transactions.',
      },
      {
        title: 'Decentralization',
        content:
          'The MATRIX AI Network is decentralized, allowing for a more secure and transparent way to conduct transactions and access AI services.',
      },
      {
        title: 'AI integration',
        content:
          'The MATRIX AI Network uses advanced AI technologies to improve network perforCOLEce and security, as well as to provide access to AI services.',
      },
    ],
  },
  {
    title: 'Where can I get $COLE coins?',
    desc: 'COLE listed on kucoin and mexc',
    list: [],
  },
]

const learnMoreList = [
  DocPng,
  'https://www.matrix.io/wp-content/uploads/2022/12/cmccom.webp',
  'https://www.matrix.io/wp-content/uploads/2022/12/medium-_1_.webp',
]

const animationFlag: any = ref({
  c0: false,
  c1: false,
  c2: false,
  c3: false,
  c4: false,
  c5: false,
  c6: false,
  c7: false,
  c8: false,
  c9: false,
  c10: false,
  c11: false,
  c12: false,
  c13: false,
  c14: false,
  c15: false,
  c16: false,
  c17: false,
  c18: false,
  c19: false,
})

const onScroll = () => {
  const selectContent = document.getElementsByClassName('animation')
  const avaheight = window.screen.availHeight
  const scrollY = window.scrollY
  if (selectContent && selectContent.length) {
    const length = selectContent.length
    for (let i = 0; i < length; i++) {
      const domRect = selectContent[i].getBoundingClientRect()
      if (domRect.top > 0) {
        if (domRect.top < 0.7 * avaheight && scrollY > 20) {
          animationFlag.value[`c${i}`] = true
        }
      }
      if (domRect.bottom < 0) {
        animationFlag.value[`c${i}`] = false
      }
      if (scrollY < 20) {
        animationFlag.value[`c${i}`] = false
      }
    }
  }
}

onMounted(() => {
  timer.value = setInterval(() => {
    currentIndex.value = currentIndex.value + 1
    if (currentIndex.value > sloganList.length - 1) {
      currentIndex.value = 0
    }
    blockChainIndex.value = blockChainIndex.value + 1
    if (blockChainIndex.value > blockChainList.length - 1) {
      blockChainIndex.value = 0
    }
    window.addEventListener('scroll', debounce(onScroll, 50))
  }, 1500)
})

onUnmounted(() => {
  clearInterval(timer.value)
  window.removeEventListener('scroll', debounce(onScroll, 50))
})
</script>

<template>
  <div class="w-screen">
    <div class="h-screen w-screen main">
      <div class="background-video">
        <video
          autoplay
          muted
          playsinline
          loop
          class="screenVideo"
          poster="https://www.matrix.io/wp-content/uploads/2023/02/photo_2023-02-06_18-42-18-3.webp"
        >
          <source src="/src/assets/video/manhead.mp4" type="video/mp4" />
        </video>
      </div>
      <div class="section-container">
        <img src="/src/assets/logo.png" class="h-20" />
        <div class="text-white text-3xl flex">
          <div class="mr-3">This is</div>
          <div :class="solganAnimationList[currentIndex % 2]">
            {{ sloganList[currentIndex] }}
          </div>
        </div>
        <div class="itemList">
          <div v-for="(item, index) in itemList" :key="index" class="item">
            <div>
              <svg>
                <use :xlink:href="`#icon-${item.logo}`"></use>
              </svg>
            </div>
            <div>
              <div class="label">{{ item.label }}</div>
              <div class="value">{{ item.value }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="coming">
      <div class="container text-center">
        <div
          class="text-white text-4xl pt-24 pb-16 textShadow animation animate__animated w-fit m-auto break-all font-bold"
          :class="animationFlag.c0 ? 'animate__fadeIn' : 'animate__fadeOut'"
        >
          COLOTE 3.0 is COMING
        </div>
        <div class="comingList pb-24">
          <div v-for="(item, index) in versionList" :key="index" class="item">
            <div>{{ item.label }}</div>
            <div>
              <svg>
                <use :xlink:href="`#icon-${item.logo}`"></use>
              </svg>
            </div>
          </div>
        </div>
        <div class="text-video">
          <div class="left">
            <div class="title text-3xl">
              Transforming Brain Waves <br />
              into<span class="text-4xl mx-1">CODE</span> with AI
            </div>
            <div class="left-content text-2xl">
              AvI is short for Avatar Intelligence. While AI focuses on training
              machines to have similar capacities as huCOLE beings, AvI aims to
              realize the scenario imagined by the COLOTE films where huCOLE
              brain is uploaded to the Internet, or where a program identical to
              a user's brain is created on the Internet.
            </div>
          </div>
          <div class="right">
            <div class="right-video">
              <iframe
                class="iframe-video"
                src="https://player.vimeo.com/video/781798549?h=1f1e3be1ba&dnt=1&app_id=122963&autoplay=1&controls=0&loop=1&muted=1"
                width="100%"
                height="100%"
                frameborder="0"
                allow="autoplay; fullscreen; picture-in-picture"
                allowfullscreen
              >
              </iframe>
            </div>
          </div>
        </div>

        <div class="text-video">
          <div class="right" style="justify-content: flex-start">
            <div class="right-video">
              <iframe
                class="iframe-video"
                src="https://player.vimeo.com/video/781811699?h=877b9fdc89&dnt=1&app_id=122963&autoplay=1&controls=0&loop=1&muted=1"
                width="100%"
                height="100%"
                frameborder="0"
                allow="autoplay; fullscreen; picture-in-picture"
                allowfullscreen
              >
              </iframe>
            </div>
          </div>
          <div class="left" style="text-align: right">
            <div class="title text-3xl">
              Distribution of Neural Data<br />
              on COLOTE Blockchain
            </div>
            <div class="left-content text-2xl">
              COLOTE 3.0 will build a general-purpose platform around Avatar
              Intelligence. Any user can use the tools on COLOTE to upload and
              store their brain wave data to create their individual avatars
              through Avatar Intelligence powered by COLOTE’s distributed
              computing.
            </div>
          </div>
        </div>
        <div class="text-video">
          <div class="left">
            <div
              class="title text-3xl animation animate__animated"
              :class="animationFlag.c1 ? 'animate__fadeIn' : 'animate__fadeOut'"
            >
              Complete control of<br />
              <span class="text-4xl">Digital</span> Avatar
            </div>
            <div class="left-content text-2xl">
              Everyone will have his/her own digital avatar in the Metaverse.
              This avatar can be used to live life and do various tasks in the
              Metaverse under users authorisation. This is the ultimate use
              scenario of the Metaverse.
            </div>
          </div>
          <div class="right">
            <div class="right-video">
              <iframe
                class="iframe-video"
                src="https://player.vimeo.com/video/781805219?h=1ffd215417&dnt=1&app_id=122963&autoplay=1&controls=0&loop=1&muted=1"
                width="100%"
                height="100%"
                frameborder="0"
                allow="autoplay; fullscreen; picture-in-picture"
                allowfullscreen
              >
              </iframe>
            </div>
          </div>
        </div>
        <div
          class="feature-img animation animate__animated"
          :class="animationFlag.c2 ? 'custom_slideInUp' : 'custom_slideInDown'"
        >
          <img src="/src/assets/image/feature.png" />
        </div>
        <div
          class="text-white text-4xl pt-24 pb-16 textShadow wow slideInLeft w-fit m-auto break-all font-bold"
          data-wow-duration="1s"
          data-wow-delay="1s"
        >
          THE FOUR PHASES OF COLOTE 3.0
        </div>
        <div class="phases-carousel">
          <el-carousel
            :interval="5000"
            arrow="hover"
            loop
            pause-on-hover
            autoplay
            height="400px"
            indicator-position="none"
            @change="handleChangeCarousel"
          >
            <el-carousel-item v-for="item in phasesList" :key="item.title">
              <div class="phases-container">
                <div>
                  <img :src="item.logo" class="phases-container-logo" />
                </div>
                <div class="phases-right">
                  <div class="text-white text-4xl mb-12">{{ item.title }}</div>
                  <div class="text-white text-2xl">{{ item.content }}</div>
                </div>
              </div>
            </el-carousel-item>
          </el-carousel>
          <el-progress
            :percentage="(currentCarouselIndex + 1) * 25"
            class="my-progress"
            color="#2563eb"
            :show-text="false"
          />
        </div>
        <div
          class="feature-img animation animate__animated"
          :class="animationFlag.c3 ? 'custom_slideInUp' : 'custom_slideInDown'"
        >
          <img
            src="https://www.matrix.io/wp-content/uploads/2022/12/phase1-2.webp"
          />
        </div>
      </div>
    </div>
    <div class="ai-network">
      <div class="container">
        <div class="text-4xl text-[#06F] text-center font-bold mb-6">
          The COLOTE AI Network makes artificial intelligence accessible to
          everything!
        </div>
        <div
          class="ai-network-list animation animate__animated"
          :class="animationFlag.c4 ? 'custom_slideInUp' : 'custom_slideInDown'"
        >
          <div v-for="(item, index) in aiNetWorkList" :key="index">
            <img :src="item.logo" class="ai-network-list-img" />
            <div class="text-3xl text-[#06f] text-center">{{ item.title }}</div>
          </div>
        </div>
        <div
          class="block-chain animation animate__animated"
          :class="animationFlag.c5 ? 'custom_slideInUp' : 'custom_slideInDown'"
        >
          <div class="block-chain-left">
            <div
              class="text-3xl text-[#ADC0FC] text-center flex justify-center max-w-[100%] break-all"
            >
              Blockchain for
              <div
                :class="solganAnimationList[blockChainIndex % 2]"
                class="ml-3"
              >
                {{ blockChainList[blockChainIndex] }}
              </div>
            </div>
            <div class="text-[#C0D1FD] text-xl mt-4">
              The COLOTE 1.0 blockchain platform is the first AI-optimised
              blockchain platform. Low transaction speeds, lack of security, the
              complexity of usage, and squandered resources are four key
              concerns in blockchain that we address with AI technology. We
              built a public blockchain platform that is both functional and
              dependable.
            </div>
          </div>
          <div class="block-chain-right">
            <img
              src="https://www.matrix.io/wp-content/uploads/2022/12/stake.webp"
              alt="main"
            />
            <div class="cole">Stake $COLE</div>
          </div>
        </div>
        <div
          class="desc2 animation animate__animated"
          :class="animationFlag.c6 ? 'custom_slideInUp' : 'custom_slideInDown'"
        >
          The COLOTE 2.0 is constructing a blockchain-based AI economy based on
          data, computer power, and AI models. We're building a self-evolving AI
          platform with aggregated processing power, safe data COLEagement,
          transparent data sharing, and access to an ever-growing set of
          on-chain AI data, models, and applications.
        </div>
        <div
          class="tab-list animation animate__animated"
          :class="animationFlag.c7 ? 'custom_slideInUp' : 'custom_slideInDown'"
        >
          <div
            v-for="(item, index) in COLEasList"
            :key="index"
            class="tab"
            :class="tabIndex == index && 'active'"
            @click="tabIndex = index"
          >
            {{ item.tab }}
          </div>
        </div>
        <div
          class="block-chain animation animate__animated"
          :class="animationFlag.c8 ? 'custom_slideInUp' : 'custom_slideInDown'"
        >
          <div class="tab-content-left">
            <img :src="COLEasList[tabIndex].logo" />
          </div>
          <div class="px-5">
            <div class="text-center text-xl text-[#333] font-bold mb-4">
              {{ COLEasList[tabIndex].title }}
            </div>
            <div class="tab-content-list">
              <div
                v-for="listItem in COLEasList[tabIndex].list"
                :key="listItem"
                class="flex mt-3 items-center"
              >
                <img
                  src="/src/assets/image/check.png"
                  style="width: 25px; min-width: 25px; height: 25px"
                  class="mr-3"
                />
                <div class="text-xl">{{ listItem }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="union-container">
      <div class="container">
        <div class="text-center text-2xl text-[#ADC0FC] pb-4">
          In union there is strength
        </div>
        <el-carousel
          :interval="5000"
          arrow="hover"
          loop
          pause-on-hover
          autoplay
          indicator-position="none"
          type="card"
          height="620px"
        >
          <el-carousel-item
            v-for="item in unionList"
            :key="item.name"
            class="card-carousel"
          >
            <div class="text-[#ADC0FC]">{{ item.content }}</div>
            <div>
              <img :src="item.logo" class="avatar" />
              <div class="text-white font-bold text-xl">
                {{ item.name }}
              </div>
              <div class="text-xl mt-2 text-[#ADC0FC]">{{ item.official }}</div>
            </div>
          </el-carousel-item>
        </el-carousel>
        <div class="joinUs" style="margin-top: 2rem">Join Us</div>
        <div class="mt-20 block-chain">
          <div class="frequently-left">
            <div class="text-[#06f] text-2xl mb-4 font-bold">
              Frequently Asked Questions
            </div>
            <el-collapse>
              <el-collapse-item
                v-for="(item, index) in frequentlyList"
                :key="item.title"
                :name="index"
                :title="item.title"
              >
                <div v-if="item.desc" class="text-[1.1rem] mb-4">
                  {{ item.desc }}:
                </div>
                <ul>
                  <li
                    v-for="(listItem, listIndex) in item.list"
                    :key="listIndex"
                    class="my-list"
                  >
                    <div class="text-[1rem] mb-2">
                      <b class="mr-2">{{ listItem.title }}:</b
                      >{{ listItem.content }}
                    </div>
                  </li>
                </ul>
              </el-collapse-item>
            </el-collapse>
            <div class="joinUs" style="margin: 20px 0 0 0">Read More</div>
            <img
              src="https://www.matrix.io/wp-content/uploads/2023/08/CoinGecko.png"
              style="height: 100px"
            />
            <img
              src="https://www.matrix.io/wp-content/uploads/2023/08/CoinMarketCap.png"
              style="height: 100px"
            />
          </div>
          <div>
            <div class="text-[#06f] text-2xl mb-4 font-bold">
              Learn More About COLOTE
            </div>
            <div class="learn-more">
              <div
                v-for="(item, index) in learnMoreList"
                :key="item"
                :class="`learn-more-${index}`"
              >
                <img :src="item" class="learnMore-img" />
              </div>
            </div>
          </div>
        </div>
        <div class="text-3xl text-[#06f] text-center mb-20 font-bold">
          Strategic Investors
        </div>
        <div class="logo-list mb-20">
          <img
            src="https://www.matrix.io/wp-content/uploads/2023/04/03.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2023/04/logo.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2023/04/Basliksiz-2.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2023/04/Tata_logo.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2023/04/Basliksiz-1.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2023/04/Basliksiz-3.png"
            alt=""
          />
        </div>
        <div class="text-3xl text-[#06f] text-center mb-20 font-bold">
          Partners
        </div>
        <div class="logo-list">
          <img
            src="https://www.matrix.io/wp-content/uploads/2023/06/14461512.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2022/10/PARTNER.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2022/10/partner1-1.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2022/10/partner2-1.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2022/10/partner3.png"
            alt=""
          />
          <img
            src="https://www.matrix.io/wp-content/uploads/2022/10/partner4.png"
            alt=""
          />
        </div>
        <div class="logo-list mt-20">
          <a href="www.baidu.com" target="_blank"
            ><img src="/src/assets/image/twitter.png" class="contact-img"
          /></a>
          <a href="www.baidu.com" target="_blank"
            ><img src="/src/assets/image/telegram.png" class="contact-img"
          /></a>
        </div>
        <div class="copy-right mt-20 pb-10 text-center text-white">
          @2022 COLOTE Foundation
        </div>
      </div>
    </div>
    <el-backtop :right="100" :bottom="100" />
  </div>
</template>

<style scoped>
.main {
  position: relative;
  width: 100%;
  background-position: center center;
  background-size: cover;
  overflow: hidden;
}

.background-video {
  z-index: -1;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  overflow: hidden;
}

.screenVideo {
  width: 100%;
  height: 100%;
  left: -0;
  top: -0;
  object-fit: cover;
  object-position: center center;
}
.section-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  justify-content: flex-end;
  padding-bottom: 80px;
  gap: 80px;
  @media screen and (max-width: 700px) {
    padding-bottom: 50px;
    gap: 50px;
  }
}
.section-container .itemList {
  width: 1120px;
  max-width: 100%;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  row-gap: 20px;
  column-gap: 40px;
  @media screen and (max-width: 1200px) {
    grid-template-columns: repeat(2, 1fr);
    padding: 0 12px;
  }
  @media screen and (max-width: 700px) {
    grid-template-columns: repeat(1, 1fr);
    padding: 0 12px;
  }
}
.item {
  width: 100%;
  border-radius: 9999px;
  border: 2px solid #06f;
  box-shadow: 1px 1px 25px 0px #0167ff;
  font-size: 1.2rem;
  color: #06f;
  transition: all 0.5s;
  cursor: pointer;
  background-color: #172c67e0;
  position: relative;
  padding: 0.8rem 0;
  display: flex;
  justify-content: center;
  gap: 1rem;
  align-items: center;
}
.item svg {
  fill: #06f;
  width: 2.5rem;
  height: 2.5rem;
  transition: all 0.5s;
}
.section-container .item:hover {
  transform: scale(1.1);
  color: #fff;
}
.section-container .item:hover svg {
  fill: #fff;
}
.section-container .item::after {
  position: absolute;
  width: 50px;
  height: 50px;
  content: '';
  display: block;
  mask-repeat: no-repeat;
  mask-size: 100% 100%;
  transition: all 0.5s;
  color: #fff;
}
.coming {
  background: #090e29;
}
.textShadow {
  text-shadow: 2px 2px 25px #003cff;
}
.comingList {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  @media screen and (max-width: 500px) {
    flex-direction: column;
  }
}
.comingList .item {
  max-width: 250px;
  background: transparent;
}
.comingList .item svg {
  width: 2rem;
  height: 2rem;
}
.comingList .item:hover {
  background-color: #06f;
  color: #fff;
}
.comingList .item:hover svg {
  fill: #fff;
  margin-left: 10px;
}
.text-video {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  text-align: left;
  row-gap: 20px;
  column-gap: 20px;
  padding-bottom: 100px;
  @media screen and (max-width: 1200px) {
    grid-template-columns: repeat(1, 1fr);
  }
}

.text-video .title {
  color: #adc0fc;
  font-weight: 600;
  margin-bottom: 2rem;
}
.text-video .left-content {
  color: #fff;
  line-height: 2.4rem;
}
.text-video .right {
  position: relative;
  display: flex;
  justify-content: flex-end;
  @media screen and (max-width: 1200px) {
    justify-content: center !important;
  }
}
.text-video .right-video {
  position: relative;
  width: 25rem;
  height: 25rem;
  max-width: 100%;
  box-shadow: 1px 1px 75px 0px #06f;
  border-radius: 2rem;
  overflow: hidden;
}
.iframe-video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.feature-img {
  padding-bottom: 4rem;
}
.feature-img img {
  width: 100%;
  object-fit: contain;
}
.phases-container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  text-align: left;
}
.phases-container-logo {
  height: 20rem;
  object-fit: contain;
}
.phases-right {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.phases-carousel {
  position: relative;
  margin-bottom: 4rem;
}
.my-progress {
  position: absolute;
  bottom: 0;
  width: 100%;
}
::v-deep .el-progress-bar__outer {
  background-color: #000;
}
.ai-network {
  padding: 100px 12px;
  background: #f9fafb;
}
.ai-network-list {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  row-gap: 20px;
  column-gap: 20px;
  @media screen and (max-width: 900px) {
    grid-template-columns: repeat(2, 1fr);
  }
}

.ai-network-list-img {
  max-width: 100%;
  transition: all 0.5s;
  cursor: pointer;
}
.ai-network-list-img:hover {
  transform: scale(1.2);
}
.block-chain {
  display: grid;
  margin: 40px 0 60px 0;
  grid-template-columns: repeat(2, 1fr);
  row-gap: 20px;
  column-gap: 20px;
  @media screen and (max-width: 900px) {
    grid-template-columns: repeat(1, 1fr);
  }
}
.block-chain-left {
  background: linear-gradient(
    81deg,
    rgba(9, 27, 174, 1) 0%,
    rgba(34, 91, 223, 1) 100%
  );
  border-radius: 1rem;
  padding: 5rem 3rem;
}
.block-chain-right {
  background: #fff;
  border-radius: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
}
.block-chain-right img {
  height: 15rem;
  object-fit: contain;
  transition: all 0.5s;
}
.block-chain-right img:hover {
  transform: scale(1.2) rotate(25deg);
}
.cole {
  box-shadow: 1px 1px 25px 0px #0167ff;
  color: #06f;
  background: #fff;
  transition: all 0.5s;
  border-radius: 9999px;
  cursor: pointer;
  width: fit-content;
  padding: 12px 24px;
}
.cole:hover {
  color: #fff;
  background: #06f;
}
.desc2 {
  max-width: 854px;
  text-align: justify;
  color: #425466;
  font-size: 1.4rem;
  font-weight: 400;
  margin: 0 auto;
}
.tab-list {
  display: flex;
  border-radius: 6px;
  margin: 40px auto;
  justify-content: center;
  overflow: auto;
  max-width: 100%;
  @media screen and (max-width: 900px) {
    justify-content: flex-start;
  }
}
.tab-list .tab {
  background: #fff;
  transition: all 0.5s;
  color: #000;
  font-weight: bold;
  font-size: 1.1rem;
  border-right: 1px solid #e5e7eb;
  padding: 14px 30px;
  cursor: pointer;
  min-width: fit-content;
}
.tab-list :first-child {
  border-radius: 6px 0 0 6px;
}
.tab-list :last-child {
  border-right: none;
  border-radius: 0 6px 6px 0;
}
.tab-list .tab:hover {
  background-color: #0066ff3d;
}
.tab-list .active:hover {
  background-color: #06f;
}
.tab-list .active {
  background-color: #06f;
  color: #c0e3ff;
  border-right: 1px solid #fff;
}
.union-container {
  background: #090e29;
  padding-top: 20px;
}
.card-carousel .avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  margin: 20px 0;
}
::v-deep .el-carousel__item--card {
  background: #0f2ab9;
  padding: 30px 25px;
  border-radius: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.joinUs {
  box-shadow: 1px 1px 25px 0px #0167ff;
  color: #06f;
  padding: 12px 20px;
  border-radius: 999px;
  margin: 0 auto;
  width: fit-content;
  cursor: pointer;
}
.joinUs:hover {
  background: #06f;
  color: #fff;
}
::v-deep .el-collapse-item__header {
  background-color: transparent;
  border-bottom-color: #0066ff5c;
  color: #adc0fc;
  font-size: 1.25rem;
}
::v-deep .el-collapse-item__wrap {
  background-color: transparent;
  border-block-color: transparent;
}
::v-deep .el-collapse-item__content {
  color: #fff;
}
::v-deep .el-collapse {
  border: none;
}
::v-deep .el-collapse-item__header.is-active {
  color: #06f;
}
.my-list {
  padding-left: 2rem;
  position: relative;
}
.my-list::before {
  content: '';
  display: inline-block;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  border: 1px solid #fff;
  position: absolute;
  top: 10px;
  left: 13px;
}
.learn-more {
  height: 560px;
  overflow-x: hidden;
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.learn-more div {
  flex-basis: 135%;
  transition: all 0.5s;
  transform-origin: center top;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  flex-grow: 1;
  flex-basis: 100%;
  position: relative;
  overflow: hidden;
  height: 100%;
  transition-timing-function: ease;
  transition-property: all;
  z-index: 1;
  cursor: pointer;
}
.learn-more div:hover {
  flex-basis: 1000%;
}
.learnMore-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.logo-list {
  display: flex;
  gap: 10px;
  overflow-x: auto;
  overflow-y: hidden;
  height: 60px;
  align-items: center;
  @media screen and (min-width: 1000px) {
    justify-content: center;
  }
}
.logo-list img {
  width: fit-content;
  height: 50px;
  object-fit: contain;
  display: inline-block;
}
.contact-img {
  transition: all 0.5s;
  cursor: pointer;
}
.contact-img:hover {
  transform: scale(1.1);
}
.animation {
  transition: all 0.5s;
}
.custom_slideInUp {
  transform: translate(0, 0);
  opacity: 1;
}
.custom_slideInDown {
  transform: translate(0, 50px);
  opacity: 0;
}
::v-deep .el-backtop {
  background: #06f;
  color: #fff;
}
</style>
