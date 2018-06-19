---
title: BizTalk Adapter for PeopleSoft Enterprise 的架構 |Microsoft 文件
description: 描述如何接收訊息，訊息時，如何驗證，並提供元件介面方法的資訊，與 BizTalk Server 使用 PeopleSoft 配接器時
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f246e974-a082-430c-ad15-23a5e597738b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb0f43dacdbd6036ef59fa3fe16102d4fe12379
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013693"
---
# <a name="peoplesoft-enterprise-adapter-architecture"></a>PeopleSoft Enterprise 配接器架構
在 Microsoft BizTalk Adapter for PeopleSoft Enterprise 基本作業期間，配接器會從 BizTalk Server 收到 XML 訊息， 然後將 XML 訊息包在 SOPA 信封中。 BizTalk Adapter for PeopleSoft Enterprise 將這些 SOAP 要求轉送至伺服器。 此配接器會使用 PeopleSoft psjoa 類別與 PeopleSoft 系統進行通訊，這些類別會透過 Jolt 傳輸通訊協定連接至 PeopleSoft 系統。 PeopleSoft 系統收到要求，並執行商務邏輯。 回覆會透過類似的程序送回。  
  
 ![](../core/media/psadapter-01-architecture.gif "PSAdapter_01_Architecture")  

  
## <a name="component-interface-methods"></a>元件介面方法  
 PeopleSoft 元件介面所提供的基本 API 本質上是低階的。 用戶端需要多次叫用這些 API。 例如，若要取得某個元件介面執行個體的屬性，用戶端需要進行一或多個呼叫來設定索引鍵值，然後再呼叫低階 Get 方法。 它必須接著傳送多個呼叫以取得屬性。 BizTalk Adapter for PeopleSoft Enterprise 新提供一組標準方法 (Get、Create、Find 和 Update)，讓用戶端只需要進行一次呼叫，就能達到相同的結果。 這是讓 BizTalk Adapter for PeopleSoft Enterprise 代表用戶端執行多次呼叫來達成。 如需這類方法的詳細資訊，請參閱[附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)。  
  
 為了建立 PeopleSoft 的結構描述，BizTalk Adapter for PeopleSoft Enterprise 會擷取 PeopleSoft 元件介面定義或中繼資料。  
  
 BizTalk Adapter for PeopleSoft Enterprise 是以傳送功能的元件介面為基礎，不需要使用 PeopleSoft Integration Broker。 這些元 件介面會公開為可從 BizTalk Server 存取的 Web 服務。  
  
### <a name="validation"></a>驗證  
 BizTalk Adapter for PeopleSoft Enterprise 從 BizTalk Server 收到 XML 訊息時，會執行兩個層級的驗證：  
  
-   XML 訊息必須符合相關 XML 規格。  
  
-   XML 訊息必須符合特定 Web 服務的要求 (例如，如資料型別之類的介面比對)。  
  
> [!NOTE]
>  不會有商務邏輯方面的驗證 (這是 PeopleSoft 系統的領域，BizTalk Adapter for PeopleSoft Enterprise 可清楚辨認該驗證)。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   