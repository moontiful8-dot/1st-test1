import React, { useState, useEffect } from 'react';
import { ShoppingBag, Menu, X, ChevronRight, Check, Droplet, Shield, Zap, Star, ArrowRight, Beaker, Leaf, RefreshCw, Truck, Gift, Heart, BarChart3, Microscope } from 'lucide-react';

// --- 서브 페이지 컴포넌트들 ---

// 1. 상품 페이지 (Products)
const ProductPage = () => (
  <div className="pt-32 pb-20 max-w-7xl mx-auto px-4">
    <div className="text-center mb-16">
      <h2 className="text-4xl font-bold text-gray-900 mb-4">Line-up Collection</h2>
      <p className="text-xl text-gray-600">당신의 옷감과 피부 타입에 맞는 최적의 솔루션을 찾으세요.</p>
    </div>
    
    {/* 필터링 UI */}
    <div className="flex justify-center gap-4 mb-12 flex-wrap">
      {['전체', '유아용', '실내건조', '스포츠'].map((filter, idx) => (
        <button key={idx} className={`px-6 py-2 rounded-full border ${idx === 0 ? 'bg-[#006D77] text-white border-[#006D77]' : 'bg-white text-gray-600 border-gray-300 hover:border-[#006D77] hover:text-[#006D77]'} transition-colors`}>
          {filter}
        </button>
      ))}
    </div>

    {/* 상품 그리드 */}
    <div className="grid md:grid-cols-3 gap-8">
      {[
        { name: '시그니처 울트라 워시', tag: 'Best', desc: '온 가족을 위한 완벽한 올인원', price: '24,000원', subPrice: '구독가 19,200원' },
        { name: '퓨어 베이비 케어', tag: 'New', desc: '신생아를 위한 무향/무자극', price: '28,000원', subPrice: '구독가 22,400원' },
        { name: '스포츠 테크 프로', tag: null, desc: '땀 냄새와 얼룩 강력 제거', price: '26,000원', subPrice: '구독가 20,800원' },
      ].map((product, idx) => (
        <div key={idx} className="group bg-white rounded-2xl border border-gray-100 overflow-hidden hover:shadow-xl transition-all duration-300">
          <div className="bg-gray-100 aspect-square relative overflow-hidden">
             <div className="absolute inset-0 bg-gray-200 flex items-center justify-center text-gray-400">
               [상품 이미지 {idx+1}]
             </div>
             {product.tag && (
               <div className="absolute top-4 left-4 bg-[#FF6B6B] text-white text-xs font-bold px-3 py-1 rounded-full">
                 {product.tag}
               </div>
             )}
             <div className="absolute bottom-0 left-0 w-full bg-white/90 backdrop-blur-sm p-4 translate-y-full group-hover:translate-y-0 transition-transform">
               <button className="w-full bg-[#006D77] text-white py-3 rounded-lg font-bold">장바구니 담기</button>
             </div>
          </div>
          <div className="p-6">
            <h3 className="text-xl font-bold text-gray-900 mb-2">{product.name}</h3>
            <p className="text-sm text-gray-500 mb-4">{product.desc}</p>
            <div className="flex justify-between items-end">
              <div>
                <span className="text-lg font-bold text-gray-900 block">{product.price}</span>
                <span className="text-sm text-[#006D77] font-semibold">{product.subPrice}</span>
              </div>
              <div className="text-yellow-400 flex text-sm">★★★★★ (4.9)</div>
            </div>
          </div>
        </div>
      ))}
    </div>
  </div>
);

// 2. 기술력 페이지 (Tech-Lab)
const TechPage = () => (
  <div className="pt-32 pb-20 bg-gray-50">
    <div className="max-w-7xl mx-auto px-4">
      <div className="text-center mb-16">
        <h2 className="text-4xl font-bold text-gray-900 mb-4">Our Science</h2>
        <p className="text-xl text-gray-600">자연에서 찾고, 과학으로 완성했습니다.</p>
      </div>

      <div className="grid lg:grid-cols-2 gap-16 items-center mb-24">
        <div className="bg-white p-8 rounded-3xl shadow-sm border border-gray-100">
          <Microscope size={48} className="text-[#006D77] mb-6" />
          <h3 className="text-2xl font-bold mb-4">Nano-Enzyme Technology</h3>
          <p className="text-gray-600 leading-relaxed mb-6">
            일반 효소보다 1/1000 크기로 쪼갠 나노 효소가 섬유 깊숙한 곳의 오염 입자만을 특정하여 분해합니다. 
            옷감 손상을 최소화하면서도 얼룩 제거율을 30% 이상 향상시켰습니다.
          </p>
          <ul className="space-y-3">
            {['특허 등록 제 10-2024-XXXX호', '찬물 용해력 99.9% 테스트 완료', '섬유 보호 기술 적용'].map((item, i) => (
              <li key={i} className="flex items-center text-gray-700">
                <Check size={16} className="text-[#006D77] mr-2" /> {item}
              </li>
            ))}
          </ul>
        </div>
        <div className="bg-gray-200 rounded-3xl h-96 flex items-center justify-center text-gray-500 relative overflow-hidden">
          <div className="absolute inset-0 bg-gradient-to-br from-teal-50 to-blue-50 opacity-50"></div>
          [기술 시연 영상 / 오염 분해 GIF]
        </div>
      </div>

      <div className="bg-white rounded-3xl p-12 shadow-lg text-center">
        <h3 className="text-2xl font-bold mb-8">투명한 전 성분 공개</h3>
        <div className="grid md:grid-cols-4 gap-8 text-left">
           {[
             { title: '코코넛 유래 계면활성제', desc: '자연 유래 세정 성분' },
             { title: '베이킹소다', desc: '탈취 및 표백 효과' },
             { title: '구연산', desc: '섬유 유연 및 살균' },
             { title: '식물성 글리세린', desc: '피부 보호 및 보습' }
           ].map((ing, i) => (
             <div key={i} className="border-t-2 border-[#006D77] pt-4">
               <h4 className="font-bold text-lg mb-1">{ing.title}</h4>
               <p className="text-sm text-gray-500">{ing.desc}</p>
             </div>
           ))}
        </div>
        <button className="mt-12 text-[#006D77] font-bold border-b border-[#006D77] pb-1 hover:text-[#005860]">
          EWG 등급 확인서 보기
        </button>
      </div>
    </div>
  </div>
);

// 3. 회사소개 페이지 (Company / Sustainability)
const CompanyPage = () => (
  <div className="pt-32 pb-20">
    {/* Hero */}
    <div className="max-w-7xl mx-auto px-4 mb-24 text-center">
      <span className="text-[#006D77] font-bold tracking-wider uppercase text-sm mb-2 block">Brand Story</span>
      <h2 className="text-4xl md:text-5xl font-bold text-gray-900 mb-8 leading-tight">
        세탁은 깨끗하게,<br />지구는 가볍게.
      </h2>
      <p className="text-xl text-gray-600 max-w-2xl mx-auto">
        클린테크온은 단순한 세제 회사가 아닙니다.<br/>
        우리는 지속 가능한 일상을 위한 가장 스마트한 기술을 연구합니다.
      </p>
    </div>

    {/* Mission Cards */}
    <div className="bg-[#E0F7FA] py-24">
      <div className="max-w-7xl mx-auto px-4">
         <div className="grid md:grid-cols-3 gap-8">
           <div className="bg-white p-8 rounded-2xl shadow-sm">
             <RefreshCw size={40} className="text-[#006D77] mb-6" />
             <h3 className="text-xl font-bold mb-3">Zero Waste</h3>
             <p className="text-gray-600">플라스틱 용기를 없애고, 100% 재활용 가능한 종이 팩과 리필 스테이션을 운영합니다.</p>
           </div>
           <div className="bg-white p-8 rounded-2xl shadow-sm">
             <Leaf size={40} className="text-[#006D77] mb-6" />
             <h3 className="text-xl font-bold mb-3">Carbon Footprint</h3>
             <p className="text-gray-600">초고농축 기술로 물류 부피를 1/3로 줄여 탄소 배출을 획기적으로 감소시켰습니다.</p>
           </div>
           <div className="bg-white p-8 rounded-2xl shadow-sm">
             <Heart size={40} className="text-[#FF6B6B] mb-6" />
             <h3 className="text-xl font-bold mb-3">1% For Earth</h3>
             <p className="text-gray-600">매출의 1%를 해양 정화 활동과 멸종 위기 해양 생물 보호에 기부합니다.</p>
           </div>
         </div>
      </div>
    </div>

    {/* Impact Counter */}
    <div className="max-w-7xl mx-auto px-4 py-24 text-center">
      <h3 className="text-2xl font-bold mb-12">우리가 함께 만들어낸 변화</h3>
      <div className="grid grid-cols-2 md:grid-cols-4 gap-8">
        <div>
           <div className="text-4xl font-bold text-[#006D77] mb-2">52,103</div>
           <div className="text-gray-500">줄인 플라스틱 (kg)</div>
        </div>
        <div>
           <div className="text-4xl font-bold text-[#006D77] mb-2">12,400</div>
           <div className="text-gray-500">리필 이용 횟수</div>
        </div>
        <div>
           <div className="text-4xl font-bold text-[#006D77] mb-2">8,900</div>
           <div className="text-gray-500">기부금액 (만원)</div>
        </div>
         <div>
           <div className="text-4xl font-bold text-[#006D77] mb-2">103</div>
           <div className="text-gray-500">해양 정화 활동 (회)</div>
        </div>
      </div>
    </div>
  </div>
);

// 4. 구독서비스 페이지 (Subscription)
const SubscriptionPage = () => (
  <div className="pt-32 pb-20 bg-white">
    <div className="max-w-7xl mx-auto px-4">
      <div className="text-center mb-16">
        <h2 className="text-4xl font-bold text-gray-900 mb-4">Smart Cycle Subscription</h2>
        <p className="text-xl text-gray-600">떨어질 걱정 없는 스마트한 세탁 생활, AI가 주기를 추천해드립니다.</p>
      </div>

      <div className="grid lg:grid-cols-2 gap-12 items-start">
        {/* 구독 혜택 */}
        <div className="space-y-6">
           <h3 className="text-2xl font-bold mb-6">구독 멤버십 혜택</h3>
           {[
             { icon: <Truck className="text-[#006D77]" />, text: "평생 무료 배송" },
             { icon: <Zap className="text-[#006D77]" />, text: "상시 20% 할인" },
             { icon: <Gift className="text-[#006D77]" />, text: "3회차마다 세탁조 클리너 증정" },
             { icon: <RefreshCw className="text-[#006D77]" />, text: "언제든지 건너뛰기/해지 가능" }
           ].map((item, i) => (
             <div key={i} className="flex items-center p-4 bg-gray-50 rounded-xl">
               <div className="w-10 h-10 bg-white rounded-full flex items-center justify-center shadow-sm mr-4">
                 {item.icon}
               </div>
               <span className="font-medium text-lg text-gray-800">{item.text}</span>
             </div>
           ))}
        </div>

        {/* 요금제 카드 */}
        <div className="bg-[#006D77] rounded-3xl p-8 text-white shadow-2xl relative overflow-hidden">
           <div className="absolute top-0 right-0 w-32 h-32 bg-white opacity-10 rounded-full -translate-y-1/2 translate-x-1/2"></div>
           <h3 className="text-2xl font-bold mb-2">Standard Plan</h3>
           <p className="text-teal-100 mb-8">4인 가족 기준 (월 1회 배송)</p>
           
           <div className="text-5xl font-bold mb-8">
             19,200원 <span className="text-lg font-normal text-teal-200">/ 월</span>
           </div>

           <div className="space-y-4 mb-8">
             <div className="flex justify-between border-b border-teal-700 pb-2">
               <span>시그니처 울트라 워시 (1L)</span>
               <span>1개</span>
             </div>
             <div className="flex justify-between border-b border-teal-700 pb-2">
                <span>휴대용 얼룩 제거제</span>
                <span>증정</span>
             </div>
           </div>

           <button className="w-full bg-white text-[#006D77] py-4 rounded-xl font-bold text-lg hover:bg-teal-50 transition-colors">
             지금 구독 시작하기
           </button>
           <p className="text-center text-xs text-teal-200 mt-4">첫 달 불만족 시 100% 환불 보장</p>
        </div>
      </div>
      
      {/* AI 추천 섹션 (간소화) */}
      <div className="mt-20 p-8 border border-gray-200 rounded-2xl text-center bg-gray-50">
        <h4 className="text-lg font-bold mb-4">내게 맞는 주기가 궁금하신가요?</h4>
        <div className="flex justify-center gap-4">
           <button className="px-6 py-2 bg-white border border-gray-300 rounded-lg hover:border-[#006D77]">1인 가구</button>
           <button className="px-6 py-2 bg-white border border-gray-300 rounded-lg hover:border-[#006D77]">2인 가구</button>
           <button className="px-6 py-2 bg-white border border-gray-300 rounded-lg hover:border-[#006D77]">4인 이상</button>
        </div>
      </div>
    </div>
  </div>
);


const CleanTechOnLanding = () => {
  const [isScrolled, setIsScrolled] = useState(false);
  const [isMobileMenuOpen, setIsMobileMenuOpen] = useState(false);
  const [currentPage, setCurrentPage] = useState('main'); // 라우팅 상태

  // 스크롤 감지 효과
  useEffect(() => {
    const handleScroll = () => {
      setIsScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  // 페이지 전환 함수
  const navigateTo = (page) => {
    setCurrentPage(page);
    setIsMobileMenuOpen(false);
    window.scrollTo({ top: 0, behavior: 'smooth' });
  };

  // --- 메인 페이지 섹션들 (기존 코드 모듈화) ---
  const MainHero = () => (
    <section className="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden">
        {/* Background Decorative Elements */}
        <div className="absolute top-0 right-0 w-1/2 h-full bg-[#E0F7FA] opacity-50 -z-10 rounded-bl-[100px]"></div>
        <div className="absolute top-20 left-10 w-64 h-64 bg-teal-100 rounded-full mix-blend-multiply filter blur-3xl opacity-30 animate-blob"></div>
        <div className="absolute top-40 right-10 w-64 h-64 bg-blue-100 rounded-full mix-blend-multiply filter blur-3xl opacity-30 animate-blob animation-delay-2000"></div>

        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative">
          <div className="grid lg:grid-cols-2 gap-12 items-center">
            {/* Copywriting */}
            <div className="space-y-8">
              <div className="inline-flex items-center px-3 py-1 rounded-full bg-teal-50 border border-teal-100 text-[#006D77] text-sm font-semibold mb-2">
                <span className="flex h-2 w-2 rounded-full bg-[#006D77] mr-2"></span>
                특허받은 나노 효소 기술
              </div>
              <h1 className="text-5xl lg:text-6xl font-bold leading-tight text-gray-900 tracking-tight">
                과학으로 증명된 순수함,<br />
                <span className="text-[#006D77]">잔여물 0%</span>의 시작.
              </h1>
              <p className="text-xl text-gray-600 leading-relaxed max-w-lg">
                눈에 보이지 않는 세제 찌꺼기까지 완벽하게 분해합니다.<br />
                세탁의 기준을 '향기'에서 '성분'으로 바꾸세요.
              </p>
              
              <div className="flex flex-col sm:flex-row gap-4">
                <button 
                  onClick={() => navigateTo('subscription')}
                  className="bg-[#FF6B6B] text-white px-8 py-4 rounded-lg font-bold text-lg hover:bg-[#ff5252] transition-all shadow-lg shadow-red-200 hover:shadow-xl hover:-translate-y-1 flex items-center justify-center">
                  100원 체험팩 신청하기
                </button>
                <button 
                  onClick={() => navigateTo('tech')}
                  className="bg-white text-[#006D77] border-2 border-[#006D77] px-8 py-4 rounded-lg font-bold text-lg hover:bg-teal-50 transition-all flex items-center justify-center">
                  기술력 리포트 보기
                </button>
              </div>
              
              <div className="flex items-center gap-4 text-sm text-gray-500 pt-4">
                <div className="flex -space-x-2">
                  {[1, 2, 3, 4].map((i) => (
                    <div key={i} className="w-8 h-8 rounded-full bg-gray-200 border-2 border-white flex items-center justify-center text-xs font-bold text-gray-400 overflow-hidden">
                       <img src={`/api/placeholder/32/32?text=U${i}`} alt="user" />
                    </div>
                  ))}
                </div>
                <p>현재 <span className="font-bold text-gray-800">12,403명</span>이 정기 구독 중입니다.</p>
              </div>
            </div>

            {/* Visual */}
            <div className="relative">
              <div className="relative rounded-2xl overflow-hidden shadow-2xl border-4 border-white/50">
                <div className="bg-gradient-to-br from-teal-500 to-blue-600 w-full aspect-[4/3] flex items-center justify-center relative">
                    <div className="absolute inset-0 bg-black/10"></div>
                    <div className="text-white text-center z-10 p-8">
                        <Droplet size={64} className="mx-auto mb-4 opacity-80" />
                        <p className="font-semibold text-lg">Hyper-Clean Simulation</p>
                        <p className="text-sm opacity-80">Micro-Enzyme Activation</p>
                    </div>
                    <div className="absolute bottom-4 left-4 bg-white/20 backdrop-blur px-3 py-1 rounded text-xs text-white font-mono">
                        Cleanliness: 99.9%
                    </div>
                    <div className="absolute top-4 right-4 bg-white/20 backdrop-blur px-3 py-1 rounded text-xs text-white font-mono">
                        Residue: 0.00%
                    </div>
                </div>
              </div>
              <div className="absolute -bottom-6 -left-6 bg-white p-4 rounded-xl shadow-xl border border-gray-100 flex items-center gap-3">
                <div className="bg-green-100 p-2 rounded-full text-green-600">
                  <Shield size={24} />
                </div>
                <div>
                  <p className="text-xs text-gray-500 font-bold uppercase">EWG Verified</p>
                  <p className="font-bold text-gray-900">전 성분 그린등급</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
  );

  const MainProblemSolution = () => (
    <section className="py-24 bg-gray-50">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="text-center max-w-3xl mx-auto mb-16">
            <h2 className="text-3xl font-bold text-gray-900 mb-4">왜 좋은 옷이 금방 망가질까요?</h2>
            <p className="text-xl text-gray-600">
              문제는 섬유 속에 남은 <span className="text-[#FF6B6B] font-bold underline decoration-wavy">화학 잔여물</span>입니다.
            </p>
          </div>

          <div className="grid md:grid-cols-2 gap-8 lg:gap-16 items-center">
            {/* Problem Card */}
            <div className="bg-white p-8 rounded-2xl shadow-sm border border-gray-100 relative overflow-hidden group hover:shadow-md transition-all">
              <div className="absolute top-0 left-0 w-2 h-full bg-red-400"></div>
              <h3 className="text-xl font-bold text-gray-900 mb-2 flex items-center">
                <X className="text-red-400 mr-2" /> 일반 세제
              </h3>
              <p className="text-gray-600 mb-6">헹굼 후에도 계면활성제가 남아 피부 자극과 섬유 손상을 유발합니다.</p>
              <div className="bg-gray-200 h-48 rounded-lg flex items-center justify-center text-gray-400 font-mono text-sm relative">
                  [현미경 확대 이미지: 거친 섬유 표면]
                  <div className="absolute bottom-2 right-2 text-xs bg-black/50 text-white px-2 py-1 rounded">잔여물 검출</div>
              </div>
            </div>

            {/* Solution Card */}
            <div className="bg-white p-8 rounded-2xl shadow-xl border border-[#006D77]/20 relative overflow-hidden transform md:-translate-y-4">
              <div className="absolute top-0 left-0 w-2 h-full bg-[#006D77]"></div>
              <div className="absolute top-4 right-4 bg-[#E0F7FA] text-[#006D77] text-xs font-bold px-3 py-1 rounded-full">
                CleanTechOn Solution
              </div>
              <h3 className="text-xl font-bold text-gray-900 mb-2 flex items-center">
                <Check className="text-[#006D77] mr-2" /> 클린테크온
              </h3>
              <p className="text-gray-600 mb-6">스마트 효소가 오염만 타겟팅하여 분해하고, 물과 만나면 즉시 생분해됩니다.</p>
              <div className="bg-teal-50 h-48 rounded-lg flex items-center justify-center text-[#006D77] font-mono text-sm relative border border-teal-100">
                  [현미경 확대 이미지: 매끄러운 섬유]
                  <div className="absolute bottom-2 right-2 text-xs bg-[#006D77] text-white px-2 py-1 rounded">잔여물 0%</div>
              </div>
            </div>
          </div>
        </div>
    </section>
  );

  const MainFeatures = () => (
    <section className="py-24 bg-white">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="text-center mb-16">
            <span className="text-[#006D77] font-bold tracking-wider uppercase text-sm">Technology</span>
            <h2 className="text-4xl font-bold text-gray-900 mt-2">압도적인 기술의 차이</h2>
          </div>

          <div className="grid md:grid-cols-3 gap-8">
            <div onClick={() => navigateTo('tech')} className="p-8 rounded-2xl bg-[#F9FAFB] hover:bg-[#E0F7FA] transition-all duration-300 group cursor-pointer hover:-translate-y-1">
              <div className="w-14 h-14 bg-white rounded-xl shadow-sm flex items-center justify-center text-[#006D77] mb-6 group-hover:scale-110 transition-transform">
                <Zap size={32} />
              </div>
              <h3 className="text-xl font-bold text-gray-900 mb-3">Nano-Enzyme Tech</h3>
              <p className="text-gray-600 leading-relaxed">
                섬유 손상 없이 오염만 정밀 타격합니다. 찬물에서도 99.9% 강력한 분해력을 경험하세요.
              </p>
            </div>
            <div className="p-8 rounded-2xl bg-[#F9FAFB] hover:bg-[#E0F7FA] transition-all duration-300 group cursor-pointer hover:-translate-y-1">
              <div className="w-14 h-14 bg-white rounded-xl shadow-sm flex items-center justify-center text-[#006D77] mb-6 group-hover:scale-110 transition-transform">
                <Leaf size={32} />
              </div>
              <h3 className="text-xl font-bold text-gray-900 mb-3">EWG Green Grade</h3>
              <p className="text-gray-600 leading-relaxed">
                타협하지 않는 안전 기준. 신생아 옷부터 민감한 속옷까지, 온 가족이 안심하고 사용합니다.
              </p>
            </div>
            <div className="p-8 rounded-2xl bg-[#F9FAFB] hover:bg-[#E0F7FA] transition-all duration-300 group cursor-pointer hover:-translate-y-1">
              <div className="w-14 h-14 bg-white rounded-xl shadow-sm flex items-center justify-center text-[#006D77] mb-6 group-hover:scale-110 transition-transform">
                <Beaker size={32} />
              </div>
              <h3 className="text-xl font-bold text-gray-900 mb-3">Hyper-Concentrate</h3>
              <p className="text-gray-600 leading-relaxed">
                단 한 번의 펌핑으로 충분합니다. 기존 세제 대비 1/3 사용량으로 압도적인 경제성.
              </p>
            </div>
          </div>
        </div>
    </section>
  );

  const MainSocialProof = () => (
    <section className="py-24 bg-[#006D77] text-white relative overflow-hidden">
        <div className="absolute inset-0 opacity-10" style={{ backgroundImage: 'radial-gradient(circle at 2px 2px, white 1px, transparent 0)', backgroundSize: '40px 40px' }}></div>
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
          <div className="grid lg:grid-cols-2 gap-16 items-center">
            <div>
              <h2 className="text-3xl lg:text-4xl font-bold mb-8">숫자가 증명하는<br/>깨끗함의 차이</h2>
              <div className="grid grid-cols-2 gap-8">
                <div className="border-l-4 border-[#64FFDA] pl-6">
                  <div className="text-5xl font-bold mb-1">99.9%</div>
                  <div className="text-teal-100">살균 및 항균 효과</div>
                </div>
                <div className="border-l-4 border-[#64FFDA] pl-6">
                  <div className="text-5xl font-bold mb-1">0.00</div>
                  <div className="text-teal-100">피부 무자극 지수</div>
                </div>
                <div className="border-l-4 border-[#64FFDA] pl-6">
                  <div className="text-5xl font-bold mb-1">4.9/5</div>
                  <div className="text-teal-100">고객 만족도</div>
                </div>
                <div className="border-l-4 border-[#64FFDA] pl-6">
                  <div className="text-5xl font-bold mb-1">20만+</div>
                  <div className="text-teal-100">누적 판매량</div>
                </div>
              </div>
            </div>
            <div className="bg-white text-gray-900 p-8 rounded-2xl shadow-2xl relative">
              <div className="absolute -top-6 right-8 text-6xl text-gray-200 font-serif">"</div>
              <div className="flex items-center space-x-1 text-yellow-400 mb-4">
                {[1, 2, 3, 4, 5].map(i => <Star key={i} size={20} fill="currentColor" />)}
              </div>
              <p className="text-lg leading-relaxed mb-6 font-medium">
                "아이 아토피 때문에 세제만 10번 넘게 바꿨는데, 클린테크온 정착 후 긁는 횟수가 현저히 줄었어요. 단순 세제가 아니라 과학입니다."
              </p>
              <div className="flex items-center">
                <div className="w-10 h-10 rounded-full bg-gray-200 mr-4 overflow-hidden">
                    <img src="/api/placeholder/40/40?text=U" alt="Reviewer" />
                </div>
                <div>
                  <div className="font-bold">김*수 고객님</div>
                  <div className="text-sm text-gray-500">3년 차 정기 구독 중</div>
                </div>
              </div>
            </div>
          </div>
        </div>
    </section>
  );

  return (
    <div className="font-sans text-gray-800 antialiased bg-white selection:bg-[#006D77] selection:text-white min-h-screen flex flex-col justify-between">
      
      {/* 1. Navigation Bar (공통) */}
      <nav className={`fixed w-full z-50 transition-all duration-300 ${isScrolled || currentPage !== 'main' ? 'bg-white/95 backdrop-blur-md shadow-sm py-4' : 'bg-transparent py-6'}`}>
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center">
            {/* Logo */}
            <div className="flex items-center cursor-pointer" onClick={() => navigateTo('main')}>
              <div className="w-8 h-8 rounded bg-[#006D77] flex items-center justify-center mr-2">
                <span className="text-white font-bold text-lg">C</span>
              </div>
              <span className={`text-2xl font-bold tracking-tight ${isScrolled || currentPage !== 'main' ? 'text-[#006D77]' : 'text-[#006D77]'}`}>
                CleanTech<span className="font-light">On</span>
              </span>
            </div>

            {/* Desktop Menu */}
            <div className="hidden md:flex space-x-8 items-center">
              <button onClick={() => navigateTo('company')} className={`${currentPage === 'company' ? 'text-[#006D77] font-bold' : 'text-gray-600'} hover:text-[#006D77] font-medium transition-colors`}>회사소개</button>
              <button onClick={() => navigateTo('products')} className={`${currentPage === 'products' ? 'text-[#006D77] font-bold' : 'text-gray-600'} hover:text-[#006D77] font-medium transition-colors`}>상품</button>
              <button onClick={() => navigateTo('tech')} className={`${currentPage === 'tech' ? 'text-[#006D77] font-bold' : 'text-gray-600'} hover:text-[#006D77] font-medium transition-colors`}>기술력</button>
              <button onClick={() => navigateTo('subscription')} className={`${currentPage === 'subscription' ? 'text-[#006D77] font-bold' : 'text-gray-600'} hover:text-[#006D77] font-medium transition-colors`}>구독서비스</button>
              <button onClick={() => navigateTo('subscription')} className="bg-[#006D77] text-white px-5 py-2.5 rounded-full font-semibold hover:bg-[#005860] transition-transform hover:scale-105 shadow-lg shadow-[#006D77]/20 flex items-center">
                시작하기 <ChevronRight size={16} className="ml-1" />
              </button>
            </div>

            {/* Mobile Menu Button */}
            <div className="md:hidden">
              <button onClick={() => setIsMobileMenuOpen(!isMobileMenuOpen)} className="text-gray-600 focus:outline-none">
                {isMobileMenuOpen ? <X size={28} /> : <Menu size={28} />}
              </button>
            </div>
          </div>
        </div>

        {/* Mobile Menu Dropdown */}
        {isMobileMenuOpen && (
          <div className="md:hidden absolute top-full left-0 w-full bg-white shadow-lg py-4 px-4 flex flex-col space-y-4 border-t h-screen">
            <button onClick={() => navigateTo('company')} className="text-lg font-medium text-gray-800 text-left py-2 border-b border-gray-100">회사소개</button>
            <button onClick={() => navigateTo('products')} className="text-lg font-medium text-gray-800 text-left py-2 border-b border-gray-100">상품</button>
            <button onClick={() => navigateTo('tech')} className="text-lg font-medium text-gray-800 text-left py-2 border-b border-gray-100">기술력</button>
            <button onClick={() => navigateTo('subscription')} className="text-lg font-medium text-gray-800 text-left py-2 border-b border-gray-100">구독서비스</button>
            <button onClick={() => navigateTo('subscription')} className="w-full bg-[#006D77] text-white py-3 rounded-lg font-bold mt-4">시작하기</button>
          </div>
        )}
      </nav>

      {/* 2. Main Content Area (Conditional Rendering) */}
      <main className="flex-grow">
        {currentPage === 'main' && (
          <>
            <MainHero />
            <MainProblemSolution />
            <MainFeatures />
            <MainSocialProof />
          </>
        )}
        {currentPage === 'company' && <CompanyPage />}
        {currentPage === 'products' && <ProductPage />}
        {currentPage === 'tech' && <TechPage />}
        {currentPage === 'subscription' && <SubscriptionPage />}
      </main>

      {/* 3. Footer (공통) */}
      <footer className="bg-gray-900 text-gray-400 py-12 border-t border-gray-800">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="grid md:grid-cols-4 gap-8">
            <div className="col-span-1 md:col-span-2">
              <span className="text-2xl font-bold text-white tracking-tight block mb-4">
                CleanTech<span className="font-light">On</span>
              </span>
              <p className="text-sm leading-relaxed max-w-xs mb-6">
                자연에서 찾고 과학으로 완성한 프리미엄 세제.<br/>
                지속 가능한 깨끗함을 연구합니다.
              </p>
              <div className="flex space-x-4">
                <div className="w-8 h-8 bg-gray-800 rounded flex items-center justify-center hover:bg-gray-700 cursor-pointer">F</div>
                <div className="w-8 h-8 bg-gray-800 rounded flex items-center justify-center hover:bg-gray-700 cursor-pointer">I</div>
                <div className="w-8 h-8 bg-gray-800 rounded flex items-center justify-center hover:bg-gray-700 cursor-pointer">Y</div>
              </div>
            </div>
            
            <div>
              <h4 className="text-white font-bold mb-4 uppercase text-sm tracking-wider">Company</h4>
              <ul className="space-y-2 text-sm">
                <li><button onClick={() => navigateTo('company')} className="hover:text-white transition-colors">브랜드 스토리</button></li>
                <li><a href="#" className="hover:text-white transition-colors">채용 정보</a></li>
                <li><a href="#" className="hover:text-white transition-colors">매장 찾기</a></li>
                <li><a href="#" className="hover:text-white transition-colors">제휴 문의</a></li>
              </ul>
            </div>
            
            <div>
              <h4 className="text-white font-bold mb-4 uppercase text-sm tracking-wider">Customer</h4>
              <ul className="space-y-2 text-sm">
                <li><a href="#" className="hover:text-white transition-colors">고객센터</a></li>
                <li><a href="#" className="hover:text-white transition-colors">배송 조회</a></li>
                <li><a href="#" className="hover:text-white transition-colors">자주 묻는 질문</a></li>
                <li><a href="#" className="hover:text-white transition-colors">이용약관</a></li>
              </ul>
            </div>
          </div>
          <div className="border-t border-gray-800 mt-12 pt-8 text-xs text-center">
            &copy; 2025 CleanTechOn Inc. All rights reserved.
          </div>
        </div>
      </footer>
    </div>
  );
};
