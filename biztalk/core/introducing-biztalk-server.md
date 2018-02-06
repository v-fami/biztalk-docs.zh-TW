---
title: "導入 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 01/30/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06a4a31a-eefe-4b1b-89ca-2cba2b6fa587
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4de6778bef644dc7bbfa25b46c28b36e1741ba6f
ms.sourcegitcommit: d0a1816a8dd8412906245d40c6479b08d7b3b20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="introducing-biztalk-server"></a>介紹的 BizTalk Server
繫結系統一起預期，而且範數。 조직이 서비스 지향 환경으로 발전해 나감에 따라, 개별 시스템을 하나의 일관된 전체로 통합하는 효율적인 비즈니스 프로세스를 만드는 진정한 목표를 달성할 수 있게 되었습니다.  
  
 Microsoft BizTalk Server 可讓連接各種不同的軟體，然後以圖形方式建立和修改處理程序邏輯會使用該軟體。 BizTalk Server 也可讓資訊工作者監控執行中的處理程序、與企業合作夥伴互動並執行其他業務相關工作。  
  
 BizTalk Server 中的主要新功能包括：  
  
-   응용 프로그램 배포, 모니터링 및 관리 지원 향상  
  
-   단순해진 설치  
  
-   BAM(비즈니스 활동 모니터링) 기능 향상  
  
BizTalk Server 也會使用其他 Microsoft 技術的最新版本。 建置於.NET Framework 中，並在 Microsoft Visual Studio 中裝載的開發人員工具。 針對儲存體，BizTalk Server 會使用 SQL Server。 BizTalk Server 可以在執行 64 位元 Windows 伺服器，利用較大的記憶體和其他硬體所提供的優點。  
  
## <a name="what-is-biztalk-server"></a>BizTalk Server란?  
 여러 시스템을 효과적인 비즈니스 프로세스로 결합하는 것은 어려운 문제입니다. 따라서 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]에는 다양한 기술이 포함되어 있습니다. 아래 그림은 이 제품의 주요 구성 요소를 보여 줍니다.  
  
 ![BizTalk Server 元件概觀](../core/media/d167608e-7c51-4d52-b8fa-9d4149242934.gif "d167608e-7c51-4d52-b8fa-9d4149242934")  
  
 그림에서 볼 수 있듯이 이 제품의 핵심은 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 엔진입니다. 엔진은 다음 두 개의 주요 부분으로 이루어져 있습니다.  
  
-   다양한 소프트웨어와 통신하는 기능을 제공하는 메시징 구성 요소. 여러 종류의 통신에 어댑터를 사용함으로써 엔진은 웹 서비스 등을 비롯한 다양한 프로토콜과 데이터 형식을 지원할 수 있습니다.  
  
-   그래픽 방식으로 정의된 프로세스(오케스트레이션) 생성 및 실행 지원. 엔진의 메시징 구성 요소를 기반으로 하는 오케스트레이션은 비즈니스 프로세스 전체 또는 일부를 작동하는 논리를 구현합니다.  
  
 다음을 비롯한 다른 여러 BizTalk 구성 요소를 엔진과 함께 사용할 수도 있습니다.  
  
-   복잡한 규칙 집합을 평가하는 비즈니스 규칙 엔진  
  
-   개발자와 관리자가 엔진 및 엔진이 실행하는 오케스트레이션을 모니터링하고 관리할 수 있도록 하는 그룹 허브  
  
-   Windows 시스템과 Windows가 아닌 시스템 간에 인증 정보 매핑 기능을 제공하는 Enterprise SSO(Single Sign-On) 기능  
  
 정보 근로자가 실행 중인 비즈니스 프로세스를 모니터링하는 데 사용하는 비즈니스 활동 모니터링은 이러한 토대를 기반으로 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]에 포함됩니다. 기술 용어 대신 비즈니스 정보가 표시되며 비즈니스 사용자가 표시되는 정보를 결정합니다.  
  
## <a name="connecting-diverse-systems"></a>連接不同的系統  
 오늘날 대부분의 비즈니스 프로세스는 부분적으로라도 소프트웨어를 사용합니다. 이러한 프로세스 중 일부는 하나의 응용 프로그램에서 지원되지만 다른 많은 프로세스는 다양한 소프트에어 시스템을 사용합니다. 대체로 이 소프트웨어는 서로 다른 시간과 플랫폼에서, 서로 다른 기술을 사용하여 만들어졌습니다. 이러한 비즈니스 프로세스를 자동화하려면 다양한 시스템을 연결해야 합니다.  
  
 解決這項挑戰有各種不同的名稱︰ 商務程序自動化 (BPA)、 商務程序管理 (BPM) 等等。 이름이 무엇이든 간에 응용 프로그램 통합에 가장 중요한 두 가지 시나리오가 있습니다. 한 시나리오는 단일 조직 내의 응용 프로그램을 연결하는 것으로, 흔히 EAI(엔터프라이즈 응용 프로그램 통합)이라고 합니다. B2B 통합이라는 다른 시나리오에서는 여러 조직의 응용 프로그램을 연결합니다.  
  
 아래 그림은 EAI 문제에 핵심 BizTalk Server 엔진을 적용한 간단한 예를 보여 줍니다. 이 시나리오에서는 IBM 메인프레임에서 실행 중인 재고 응용 프로그램이 항목 재고가 부족한 것을 발견하고 해당 항목을 더 주문하는 요청을 실행합니다. 이 요청은 BizTalk Server 오케스트레이션으로 전송되며(1단계), 그런 다음 오케스트레이션이 이 조직의 ERP 응용 프로그램에 구매 주문 요청을 실행합니다(2단계). Unix 시스템에서 실행 중인 ERP 응용 프로그램이 요청된 PO를 돌려보낸 다음(3단계), BizTalk Server 오케스트레이션이 .NET Framework를 사용하여 Windows에 빌드된 주문 처리 응용 프로그램에 항목을 주문해야 한다고 알립니다(4단계).  
  
 ![BizTalk 引擎中實作的 EAI。](../core/media/7d8558da-03cf-494b-8334-efe0ea15a6a7.gif "7d8558da-03cf-494b-8334-efe0ea15a6a7")  
  
 이 예에서 각 응용 프로그램은 서로 다른 프로토콜을 사용하여 통신합니다. 따라서 BizTalk Server 엔진의 메시징 구성 요소가 기본 통신 스타일로 각 응용 프로그램과 통신할 수 있어야 합니다. 또한 어떠한 단일 응용 프로그램도 전체 비즈니스 프로세스를 인식하지 못합니다. 관련된 모든 소프트웨어를 조정하는 데 필요한 인텔리전스는 BizTalk Server 오케스트레이션에서 구현됩니다.  
  
 조직 내의 응용 프로그램 연결도 중요하지만 여러 조직에 걸쳐 있는 응용 프로그램 연결은 그 이상의 가치가 있습니다. 아래 그림은 이러한 종류의 B2B 통합에 대한 간단한 예를 보여 줍니다. 이 경우 그림 맨 위의 구매 조직은 두 개의 공급자 조직과 상호 작용하는 BizTalk Server 오케스트레이션을 실행합니다. 공급자 A도 BizTalk Server를 사용하여 공급 응용 프로그램에 대한 간접 액세스를 제공합니다. 공급자 B는 다른 공급업체의 통합 플랫폼을 사용하고 웹 서비스 등을 통해 구매 조직의 BizTalk Server 오케스트레이션에 연결합니다.  
  
 ![企業對企業整合圖](../core/media/b1d8787d-e842-468e-96c5-b68875d9abc3.gif "b1d8787d-e842-468e-96c5-b68875d9abc3")  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Server](../core/understanding-biztalk-server.md)
