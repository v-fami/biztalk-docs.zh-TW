---
title: WCF 配接器常見問題集： WCF 端點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccc94b7d-b8a6-4c24-907e-922fd885b874
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ff3b506d77418a3aaa17a040fb003c9466e093e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980295"
---
# <a name="wcf-adapter-faq-wcf-endpoints"></a>WCF 配接器常見問題集：WCF 端點
## <a name="what-are-two-endpoints-options-can-be-created-by-the-biztalk-wcf-service-publishing-wizard"></a>BizTalk WCF 服務發佈精靈可以建立哪兩個端點選項？  
 當執行 BizTalk WCF 服務發佈精靈，您可以選取建立 WCF 服務端點或 WCF 僅中繼資料端點 (MEX)。  
  
 服務端點會建立實際的 WCF 服務的功能公開 （expose) 的 IIS 中裝載的實際 Web 位置。 只有外掛式配接器 （Wcf-wshttp、 Wcf-basichttp 和 Wcf-customisolated） 可用於服務端點。 這種類型的端點的功能是由協調流程或結構描述發佈為 WCF 服務實作。  
  
 僅中繼資料端點是其功能透過 BizTalk 實作的其中一個接收位置。  這會使用 IIS 和內含式 WCF 接收配接器，而不是公開的協調流程或實際的 WCF 服務程式碼。 使用精靈來產生僅中繼資料端點可提供整合的資訊更簡單的方法公開接收使用內含式 WCF 配接器比在手動使用 svcutil.exe 的位置。 使用 svcutil.exe 會強迫您有辦法讓它可以呼叫，將中繼資料轉送給您的服務的取用者。  
  
## <a name="why-would-i-use-a-metadata-only-endpoint-in-biztalk-server"></a>為什麼要使用僅中繼資料端點在 BizTalk Server？  
 透過僅中繼資料端點，服務實作中沒有實際的 WCF 服務。 相反地的功能實作中的 BizTalk 接收位置，就如同與服務端點的 WCF 服務呼叫。 例如，您可能有兩個結構描述和對應，以取得訊息中的欄位，並將它轉換成全部大寫。 在此情況下服務的中繼資料中發行為 「 ConvertToUpper"。 但在接收位置並不在程式碼或透過協調流程實作服務的功能。  
  
 WCF 端點是由位址、 繫結和合約所組成。 當精靈建立僅中繼資料端點時，它會取得位址和繫結詳細資料，從已經現有接收位置。 在 BizTalk 協調流程中可以存在的結構描述所定義的合約資訊，或您可以使用精靈，以手動方式加以建立。 如果您選擇**BizTalk 協調流程發佈為 WCF 服務**，僅為中繼資料端點使用的連接埠和訊息類型，從協調流程的組件來定義的合約。  
  
 如果您選擇**結構描述發佈為 WCF 服務**，此精靈可讓您藉由指定服務和作業的名稱與現有的輸入和輸出結構描述中定義的服務定義。 精靈會建立的.svc 檔和 IIS 虛擬目錄，因此發行後，可以瀏覽中繼資料。 BizTalk WCF 服務發佈精靈也會建立 web.config 檔案以的 httpGetEnabled 屬性\<serviceMetadata\>項目設為 true。 此發行的中繼資料瀏覽。 如果您選擇的 BizTalk 接收位置發佈服務中繼資料，該資料可以透過存取 GET 要求透過 HTTP 使用`?wsdl`服務的 URL 結尾處。  
  
## <a name="are-service-endpoints-hosted-in-iis-and-why"></a>會在 IIS 中裝載的服務端點及為何？  
 是，服務端點裝載於 IIS 使用三種外掛式配接器的其中一個：  
  
- Wcf-wshttp  
  
- WCF-BasicHttp  
  
- WCF-CustomIsolated  
  
  服務端點會不同於僅中繼資料端點，可以直接做為 WCF 服務呼叫其功能的範圍。 使用 BizTalk WCF 服務發佈精靈來建立服務端點的設定，結果中的新接收位置中指定的 BizTalk 應用程式。 它會定義協調流程可以透過 IIS 的 URI。  
  
## <a name="when-creating-a-service-endpoint-why-would-i-select-to-publish-schemas-as-a-wcf-service"></a>建立服務端點時，為什麼我會選取 「 結構描述發佈為 WCF 服務 」 以嗎？  
 選擇此選項，將結構描述發佈為 WCF 服務，如果您的 WCF 接收位置是使用僅限 BizTalk 傳訊的 BizTalk 應用程式的一部分。 這表示沒有協調流程使用，而且所有功能會公開透過接收位置和傳送埠。 結構描述會發佈到指定的合約資訊。 取得這項資訊可以從結構描述的組件，或甚至是從協調流程組件 （雖然協調流程可能不適用於此端點）。