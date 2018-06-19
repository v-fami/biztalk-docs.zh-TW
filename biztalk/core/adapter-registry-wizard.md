---
title: 配接器登錄精靈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- utilities, Adapter Registration Wizard
- Adapter Registration Wizard
ms.assetid: bd15d0c7-01bb-41f9-9157-cdcf4bb4e39a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b721294acb07d4c69c5b2ae7b58b0e135625eee8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965316"
---
# <a name="adapter-registry-wizard"></a>配接器登錄精靈
您可以使用配接器登錄精靈來建立設定和註冊自訂的配接器所需的登錄檔。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 *\<安裝路徑\>* \SDK\Utilities\AdapterRegistryWizard\  
  
## <a name="to-run-this-utility"></a>執行此公用程式  
 執行 AdapterRegistryWizard.exe 可執行檔，以啟動精靈。 接下來將會出現幾個頁面，提示您輸入有關配接器的資訊，以及配接器支援的屬性。 下列各節將描述「配接器登錄精靈」的各個頁面。  
  
### <a name="generic-adapter-properties-page"></a>一般配接器屬性頁面  
 使用 [一般配接器屬性] 頁面可指定配接器屬性。  
  
|使用|動作|  
|--------------|----------------|  
|**傳輸配接器類型**|指定配接器類型。|  
|**屬性命名空間**|指定配接器命名空間。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將配接器特定屬性儲存在這個命名空間中的訊息內容。|  
|**配接器接收訊息，並將它們送出至 BizTalk Server**|識別配接器支援的通訊模式。 用來計算配接器的 Constraints 登錄項目。|  
|**配接器可以從 BizTalk Server 傳送訊息**|識別配接器支援的通訊模式。 用來計算配接器的 Constraints 登錄項目。|  
  
### <a name="inbound-part-page"></a>輸入部分頁面  
 使用 [輸入部分] 頁面可指定配接器的輸入接收邏輯。  
  
|使用|動作|  
|--------------|----------------|  
|**瀏覽**|為您的配接器選取會實作輸入接收邏輯的組件。 此組件所公開的公用型別清單隨即出現在下拉式清單中。 請從下拉式清單中，在針對此配接器實作輸入邏輯的指定組件內，選取型別。|  
|**配接器支援要求-回應通訊協定**|指定配接器的接收功能。 用來計算配接器的 Constraints 登錄項目。|  
|**配接器是外掛式 （裝載在不同的處理序）**|指定配接器的接收功能。 用來計算配接器的 Constraints 登錄項目。|  
  
### <a name="outbound-part-page"></a>輸出部分頁面  
 使用 [輸出部分] 頁面可指定配接器的輸出接收邏輯。  
  
|使用|動作|  
|--------------|----------------|  
|**瀏覽**|為您的配接器選取會實作輸出接收邏輯的組件。 這個組件所公開的公用型別清單隨即出現在下拉式清單中。 請從下拉式清單中，在針對此配接器實作輸出邏輯的指定組件內，選取型別。 您也必須輸入用於識別通訊協定 (由此配接器所使用) 之以逗號分隔的別名清單 (例如 submit://)。|  
|**配接器支援請求-回應通訊協定**|識別配接器的傳輸功能。 這些值可用來計算配接器的 Constraints 登錄項目。|  
  
### <a name="adapter-management-page"></a>配接器管理頁面  
 使用 [配接器管理] 頁面可指定配接器的設計階段管理邏輯。  
  
|使用|動作|  
|--------------|----------------|  
|**瀏覽**|為您的配接器選取會實作設計階段配接器管理邏輯的組件。 此組件所公開的公用型別清單隨即出現在下拉式清單中。 請從下拉式清單中，在針對此配接器實作配接器管理邏輯的指定組件內，選取型別。|  
  
### <a name="output-file-name"></a>輸出檔名稱  
 使用 [輸出檔名稱] 頁面可指定輸出檔的名稱和位置。  
  
|使用|動作|  
|--------------|----------------|  
|**瀏覽**|選擇輸出檔的名稱和位置。 配接器登錄會寫入這個檔案。|  
  
## <a name="remarks"></a>備註  
 「配接器登錄精靈」公用程式會在「企業單一登入」(SSO) 組態存放區屬性中填入預設值。 如果您的配接器並未使用配接器架構提供的標準屬性頁面做為處理常式和位置配接器屬性，您必須手動編輯登錄檔來修改這些值。 如需這些設定的詳細資訊，請參閱 「 SSO 組態存放區的配接器屬性登錄 」 主題中[登錄配接器](../core/registering-an-adapter.md)。  
  
## <a name="see-also"></a>請參閱  
 [在 SDK 中的公用程式](../core/utilities-in-the-sdk.md)   
 [註冊配接器](../core/registering-an-adapter.md)