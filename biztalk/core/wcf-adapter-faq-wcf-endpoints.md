---
title: "WCF 配接器 FAQ: WCF 端點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccc94b7d-b8a6-4c24-907e-922fd885b874
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90c59c586f0d7f1d02ad406baec694cf4e22ff24
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="wcf-adapter-faq-wcf-endpoints"></a>WCF 配接器常見問題集：WCF 端點
## <a name="what-are-two-endpoints-options-can-be-created-by-the-biztalk-wcf-service-publishing-wizard"></a>BizTalk WCF 服務發佈精靈可以建立哪兩個端點選項？  
 當執行 BizTalk WCF 服務發佈精靈，您可以選取建立 WCF 服務端點或 WCF 僅為中繼資料端點 (MEX)。  
  
 服務端點建立會公開功能的實際的 WCF 服務的 IIS 中裝載的實際 Web 位置。 只有外掛式配接器 （Wcf-wshttp、 Wcf-basichttp 和 Wcf-customisolated） 可用於服務端點。 這種類型的端點的功能是由協調流程或結構描述發佈為 WCF 服務的實作。  
  
 僅為中繼資料端點是其功能透過 BizTalk 實作的其中一個接收位置。  這會使用 IIS 和內含式 WCF 接收配接器，而不是所公開的協調流程或實際的 WCF 服務程式碼。 使用精靈來產生僅中繼資料端點可提供整合的資訊更簡單的方法公開接收位置使用比使用 svcutil.exe 來手動執行內含式 WCF 配接器。 使用 svcutil.exe 會強迫您找到的中繼資料轉寄給您的服務取用者，所以可以呼叫的方法。  
  
## <a name="why-would-i-use-a-metadata-only-endpoint-in-biztalk-server"></a>為什麼要使用僅為中繼資料端點在 BizTalk Server？  
 僅為中繼資料端點與服務實作不存在於實際的 WCF 服務。 相反地，在 BizTalk 中實作功能的接收位置，就像與服務端點的 WCF 服務呼叫。 例如，您可能會有兩個結構描述及對應需要的訊息中的欄位，將它轉換為全部大寫。 在此情況下發行服務中繼資料中為"ConvertToUpper"。 但在接收位置並不在程式碼或透過協調流程實作服務的功能。  
  
 WCF 端點是由位址、 繫結及合約所組成。 當精靈建立僅為中繼資料端點時，它會取得位址和繫結詳細資料，從現有接收位置。 BizTalk 協調流程中可以存在的結構描述所定義的合約資訊，或您可以使用精靈 手動加以建立。 如果您選擇**BizTalk 協調流程發佈為 WCF 服務**，僅為中繼資料端點可用於從協調流程的組件的連接埠和訊息型別定義合約。  
  
 如果您選擇**結構描述發佈為 WCF 服務**，此精靈可讓您藉由指定服務和作業的名稱與現有的輸入和輸出結構描述中定義的服務定義。 此精靈會建立.svc 檔和 IIS 虛擬目錄，讓發行後，可以瀏覽中繼資料。 BizTalk WCF 服務發佈精靈還會建立 web.config 檔案含有其 httpGetEnabled 屬性\<serviceMetadata\>項目設為 true。 這會發行的中繼資料瀏覽。 如果您選擇 BizTalk 接收位置發佈服務中繼資料，該資料可透過 GET 要求透過 HTTP 使用`?wsdl`服務 URL 的結尾。  
  
## <a name="are-service-endpoints-hosted-in-iis-and-why"></a>IIS 中裝載的服務端點和為何？  
 是，服務端點裝載於 IIS 使用三種外掛式配接器的其中一個：  
  
-   Wcf-wshttp  
  
-   WCF-BasicHttp  
  
-   WCF-CustomIsolated  
  
 服務端點與僅為中繼資料端點的直接做為 WCF 服務可以呼叫它的功能。 使用 BizTalk WCF 服務發佈精靈來建立服務端點的設定，結果中的新接收位置中指定的 BizTalk 應用程式。 它會定義協調流程可以透過 IIS 的 URI。  
  
## <a name="when-creating-a-service-endpoint-why-would-i-select-to-publish-schemas-as-a-wcf-service"></a>建立服務端點時，為什麼我會選取 「 結構描述發佈為 WCF 服務 」 以嗎？  
 選擇結構描述發佈為 WCF 服務，如果您的 WCF 接收位置是使用僅限 BizTalk 傳訊的 BizTalk 應用程式的一部分。 這表示正在使用中，沒有協調流程，而且所有功能會公開透過接收位置和傳送埠。 結構描述會發行至指定的合約資訊。 取得這項資訊可以從結構描述的組件，或甚至是從協調流程組件 （雖然協調流程可能不適用於此端點）。