---
title: 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, schema types
- deploying, schemas
- schemas
- schemas, about schemas
- property schemas
- envelope schemas
- schemas, deploying
- XML schemas
- flat file schemas
ms.assetid: aea772bd-e7ab-448e-ba82-e7c8f38087db
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 696c79a30bb58cd91536c19c97db54d6159762b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270086"
---
# <a name="schemas"></a>結構描述
Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 XML 結構描述定義 (XSD) 語言來定義的所有訊息之處理序，並指的是這些做為訊息結構的定義結構*結構描述*。 在絕大部分的情況下，結構化訊息是所有應用程式的核心。 這些結構化訊息可以是任何形式、大小，並以一系列大範圍的後端系統和資料存放區為目標。 經常建立和消耗結構化訊息的系統使用不同的格式。 結構化訊息最常使用的兩種格式為 XML 和一般檔案。  
  
 BizTalk Server 支援下列四種類型的結構描述：  
  
-   XML 結構描述。 XML 結構描述定義 XML 執行個體訊息類別的結構。 由於這種類型的結構描述是使用 XML 結構描述定義 (XSD) 語言定義 XML 執行個體訊息的結構，而這正是 XSD 的用途，所以這類結構描述會以直接的方式使用 XSD。 如需有關 XML 結構描述的詳細資訊，請參閱[XML 結構描述](../core/xml-schemas.md)。  
  
-   一般檔案結構描述。 一般檔案結構描述是用來定義使用一般檔案格式 (分隔或位置或這兩者的組合) 的執行個體訊息類別之結構。 由於 XSD 的原生語意功能無法滿足定義一般檔案執行個體訊息結構的所有需求 (例如可用於一般檔案中不同記錄和欄位的各種分隔符號)，因此，BizTalk Server 使用了 XSD 的註解功能，將此額外資訊儲存在 XSD 結構描述中。 BizTalk Server 定義了一組豐富的特定註解標記，可用來儲存所有必要的額外資訊。 如需有關一般檔案結構描述的詳細資訊，請參閱[一般檔案結構描述](../core/flat-file-schemas.md)。  
  
-   信封結構描述。 信封結構描述是一種 XML 結構描述。 信封結構描述是用來定義 XML 信封的結構，可用來將一或多個 XML 商務文件包裝成單一 XML 執行個體訊息。 將 XML 結構描述定義為信封結構描述時，根據信封結構描述中是否定義了一個以上的根記錄而定，會需要其他的屬性設定。 如需信封結構描述的詳細資訊，請參閱[信封結構描述](../core/envelope-schemas.md)。  
  
-   屬性結構描述。 屬性結構描述是與 BizTalk Server 中所具有的兩種機制之一搭配使用，用來進行屬性升級。 *屬性升級*是執行個體訊息內特定值複製到訊息內容的程序。 透過訊息內容，這些值可以更容易被各種 BizTalk Server 元件存取。 這些元件可使用這些值來執行訊息路由等動作。 您也可以依相反方向複製升級的屬性值 (從較容易存取的訊息內容複製回執行個體訊息內)，只要是在執行個體訊息傳送到目的地之前即可。 屬性結構描述是 BizTalk 結構描述的簡單版本，在執行個體訊息與訊息內容之間來回複製升級屬性的過程中會使用到。 如需屬性結構描述的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。  
  
## <a name="schema-deployment"></a>結構描述部署  
 您會部署不同類型的結構描述，如訊息結構描述、屬性結構描述及信封結構描述。 因為每個結構描述都不同，因此在部署後處理各結構描述的方法上也有些微不同。 本節會指出所有結構描述的共同點，也會描述這些結構描述類型的不同之處。  
  
 當您部署結構描述時，管理資料庫會儲存結構描述的內容。 您可以在同一個目標命名空間內部署多個結構描述。 BizTalk Server 會在管線設計師中明確指出在執行階段使用的結構描述。 若您使用預設的管線，或您不要在管線設計師中指定結構描述，或是已經部署了同一個結構描述的多種版本，BizTalk Server 會判斷要使用的結構描述。 在此情況下，將使用以該結構描述部署的最新版本組件相關的結構描述 (具有最高的版本號碼)。  
  
 當您移除部署結構描述的最新版組件時，來自同一個組件之最高舊版本的結構描述會變成作用中的結構描述。  
  
 若您部署的結構描述有重複的目標命名空間，您必須參照來自自訂設計使用者管線的結構描述。 這樣可提供其他的資訊給傳訊引擎，來載入正確的結構描述。  
  
 例如，您會使用重複目標命名空間的一個案例是，當您建立多個 Web 服務結構描述版本時。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 編輯器建立結構描述](../core/creating-schemas-using-biztalk-editor.md)   
 [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
 [成品](../core/artifacts.md)