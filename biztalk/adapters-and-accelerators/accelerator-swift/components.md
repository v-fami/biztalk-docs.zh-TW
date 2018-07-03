---
title: 元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, components
ms.assetid: 8793534f-5bd7-4cd3-9a42-8f0895f91007
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c8595aafb14b42240a5f781faf481977be2b821
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014679"
---
# <a name="components"></a>Components
使用 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]元件實作 SWIFT 為中心的中介軟體解決方案，協助交易夥伴關聯性、 企業應用程式整合 (EAI) 和應用程式和商務工作流程自動化。 這些元件包括：  
  
- **SWIFT 的訊息結構描述。** 使用 XML 結構描述定義語言 (XSD)-相容的結構描述，以幫助的原生 SWIFT 的一般檔案訊息剖析成 XML 使用 SWIFT 管線元件和[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]執行階段。 SWIFT 的資料轉換成 XML 之後，您可以使用對應將它轉換成另一種格式，例如分隔的一般檔案或位置一般檔案。 此轉換可讓您使用現有的應用程式中的檔案。 您也可以使用這類的 XML 資料，而不需要任何對應，僅限驗證的案例。 SWIFT 結構描述也會強制 SWIFT 定義的資料和格式的規則。 如需此版本中提供的結構描述的完整清單，請參閱 <<c0> [ 支援訊息](../../adapters-and-accelerators/accelerator-swift/supported-messages.md)。  
  
- **SWIFT 的驗證原則和架構。** 您使用[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]商務規則引擎 (BRE) 原則，以驗證和加強 SWIFT 定義的資料、 格式、 網路和使用方式的規則。 SWIFT 解譯器和[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]驗證元件叫用 BRE。 驗證錯誤會收集到錯誤集合物件和錯誤訊息會以特殊的升級屬性標示再發佈至 MessageBox 資料庫。  
  
- **SWIFT 管線元件。** 您可以使用 BizTalk 管線解譯器和組合器元件來處理 SWIFT 的訊息。 SWIFT 解譯器以動態方式解析 SWIFT 的訊息類型、 反組譯 SWIFT 的訊息批次、 將訊息剖析成 XML，並驗證訊息時所依據的 SWIFT 的資料格式和網路和使用方式的規則。 SWIFT 組合器會將 XML 資料序列化至 SWIFT 的一般檔案格式。  
  
- [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]  **驗證元件。** [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]組件提供類別應用程式開發介面 (Api)，可用於 BizTalk 協調流程運算式 」 圖形。 這些類別會提供相同的 SWIFT 的訊息驗證功能 SWIFT 解譯器執行。 這項功能可讓進行中協調流程 （例如，在轉換，或修改 SWIFT 的訊息） 的訊息驗證。  
  
- **Message Repair 和 New Submission。** 您可以使用 [訊息修復和 New Submission] 功能來修復，無法通過驗證，或無法剖析 SWIFT 解譯器，訊息，或建立並提交新訊息。 這項功能透過 MrsrRepair 協調流程，MRSR SharePoint 網站，來實作和[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。  
  
- **FRR 回應對帳。** FRR 回應對帳調解 FIN 回應使用 A4SWIFT，原先傳送的訊息啟用結果訊息回應相互關聯集的自訂處理。 透過 FrrMain 協調流程實作 FRR、 FRR 接收位置和傳送埠，與 BizTalk Adapter for MQSeries。  
  
- **軟體開發套件 (SDK)。** SDK 會提供工具、 教學課程和範例，可協助開發和部署 SWIFT 為基礎的 BizTalk 解決方案。 這些解決方案包括：  
  
  -   [端對端教學課程](../../adapters-and-accelerators/accelerator-swift/end-to-end-tutorial2.md)  
  
  -   [BRE 部署公用程式](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md)  
  
  -   [SWIFT 標頭和結尾結構描述](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
- **文件。** [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] 說明描述您要規劃、 開發、 部署及維護 SWIFT 型 BizTalk 解決方案。  
  
## <a name="see-also"></a>另請參閱  
[執行階段、訊息修復、FIN 回應和傳訊](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)