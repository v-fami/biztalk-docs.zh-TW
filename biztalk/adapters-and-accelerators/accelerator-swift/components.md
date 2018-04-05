---
title: 元件 |Microsoft 文件
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
ms.openlocfilehash: 6ca9c5fdb04ffd182a8c51963c1a5c7cf5e7f8c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="components"></a>Components
您使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]元件才能實作 SWIFT 為主的中介軟體解決方案，以便交易夥伴的關聯性、 企業應用程式整合 (EAI)，和應用程式和商務工作流程自動化。 這些元件包括：  
  
-   **SWIFT 訊息結構描述。** 使用 XML 結構描述定義語言 (XSD)-標準的結構描述，以利於進行原生 SWIFT 的一般檔案訊息剖析成 XML 使用 SWIFT 管線元件和[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]執行階段。 SWIFT 的資料轉換成 XML 之後，您可以使用對應將它轉換成其他格式，例如分隔的一般檔案或位置一般檔案。 此轉換可讓您使用現有的應用程式中的檔案。 您也可以使用 XML 資料，沒有任何對應，例如，僅限驗證的案例。 SWIFT 的結構描述也會強制執行 SWIFT 定義的資料和格式的規則。 如需此版本中提供的結構描述的完整清單，請參閱[支援訊息](../../adapters-and-accelerators/accelerator-swift/supported-messages.md)。  
  
-   **SWIFT 的驗證原則和架構。** 您使用[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]商務規則引擎 (BRE) 原則，以驗證和強制執行 SWIFT 定義的資料、 格式、 網路和使用方式的規則。 SWIFT 解譯器和[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]驗證元件叫用 BRE。 收集驗證錯誤至錯誤集合物件和錯誤訊息會在發佈至 MessageBox 資料庫之前標示特殊的升級屬性。  
  
-   **SWIFT 的管線元件。** 您可以使用 BizTalk 管線解譯器和組合器元件來處理 SWIFT 的訊息。 SWIFT 解譯器以動態方式解析 SWIFT 訊息類型、 反組譯 SWIFT 訊息批次、 訊息剖析成 XML，並驗證訊息時所依據 SWIFT 資料格式和網路與使用規則。 SWIFT 組合器序列化為 XML 資料回 SWIFT 的一般檔案格式。  
  
-   [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]  **驗證元件。** [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]組件提供類別應用程式開發介面 (Api)，可用於 BizTalk 協調流程運算式 」 圖形。 這些類別會提供相同的 SWIFT 訊息驗證功能 SWIFT 解譯器執行。 這項功能可讓進行中協調流程 （例如後轉換，或修改 SWIFT 訊息）, 的訊息驗證。  
  
-   **訊息修復和新送出。** 您可以使用 [訊息修復和新送出] 功能來修復的訊息驗證失敗，或無法剖析 SWIFT 解譯器，或建立並提交新的訊息。 這項功能透過 MrsrRepair 協調流程，MRSR SharePoint 網站，來實作和[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。  
  
-   **FRR 回應對帳資料。** FRR 回應對帳調解 FIN 回應與原本 A4SWIFT，所傳送的訊息讓自訂處理程序的結果訊息回應相互關聯集。 FRR 透過 FrrMain 協調流程來實作，FRR 接收位置和傳送連接埠和 BizTalk Adapter for MQSeries。  
  
-   **軟體開發套件 (SDK)。** SDK 提供工具、 教學課程和範例，用以協助開發和部署 SWIFT 為基礎的 BizTalk 解決方案。 這些解決方案包括：  
  
    -   [端對端教學課程](../../adapters-and-accelerators/accelerator-swift/end-to-end-tutorial2.md)  
  
    -   [BRE 部署公用程式](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md)  
  
    -   [SWIFT 的標頭和結尾結構描述](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
-   **文件。** [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]說明內容說明您需要規劃、 開發、 部署和維護 SWIFT 為基礎的 BizTalk 方案。  
  
## <a name="see-also"></a>另請參閱  
[執行階段、 訊息修復、 FIN 回應和傳訊](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)