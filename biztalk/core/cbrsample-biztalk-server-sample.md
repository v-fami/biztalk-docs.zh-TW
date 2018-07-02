---
title: CBRSample （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, routing
- messages, filters
- outbound maps
- examples, messages
- messages, routing
- examples, outbound maps
- examples, filters
- messages, examples
ms.assetid: 8fba494c-9257-4eed-8b6a-867056147c2c
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b2106998a6ec7af7f2508e199bb1e4e5aa97f73
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983967"
---
# <a name="cbrsample-biztalk-server-sample"></a>CBRSample （BizTalk Server 範例）
CBRSample 範例會示範如何套用篩選條件和輸出對應，以轉換並根據內容來路由執行個體訊息。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會示範如何根據國碼，將內含名稱、地址和連絡資訊的訊息路由至兩個資料夾之一。 具體來說，本範例執行下列工作：  

1.  定義內含個人基本資訊的範例訊息格式，包括含使用者識別碼和完整名稱的身份識別、含國碼的地址，以及電話連絡資訊。  

2.  提升**CountryCode**輸入文件，因此它可以用在連接埠篩選器來控制轉換和路由中的屬性。  

3.  訊息轉換為加拿大版時**CountryCode**等於 200 或美國版本時**CountryCode**等於 100。 這兩種轉換會通過中間以外的所有資料初始 (**初始**)。 加拿大版也會對應**狀態**要**省**並**ZipCode**至**PinCode**。  

4.  將美國的訊息路由至 US 目錄，將加拿大的訊息路由至 CAN 目錄。  

## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 其設計依賴 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的預設傳送和接收 XML 管線、屬性升級、訂閱篩選器和輸出對應來路由傳送訊息。 下表列出設計元素及其原因。  


|        設計元素        |                                                                                                          已選取的原因                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 預設 XML 接收管線 | -XMLReceive 管線支援屬性升級;PassThruReceive 管線則否。<br />-輸入的訊息已經是 XML 格式，而且不需要基本解譯和合作對象解析之外的處理。 |
|      屬性升級      |          -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]依賴屬性欄位來進行路由。 辨別欄位可用於協調流程，不能用於路由。           |
|     訂閱篩選器      |                                                -訂用帳戶篩選器會執行實際的路由： 擷取符合根據屬性欄位的一或多個準則的訊息。                                                |
|         輸出對應         |                                                     對應轉換到另一個從一種格式的資料。 範例會將輸入訊息對應至美國或加拿大的格式。                                                      |
|         XMLTransmit          |                                                         -執行基本的組件的外寄 XML 訊息;PassThruTransmit 管線提供額外的支援。                                                          |

 基本模式擴充後可用於更複雜的情況。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 此範例位在 <`Samples Path>`\Messaging\CBRSample\\。  

 下表顯示此範例中的檔案，並描述其用途。  

|檔案|描述|  
|---------------|-----------------|  
|CBRDataCAN.Xml, CBRDataUS.Xml|符合 CBRInputSchema.xsd 檔案中所定義結構描述的範例輸入檔。|  
|CBRInput2CANMap.btm, CBRInput2USMap.btm|將檔案加拿大和美國格式轉換，分別對應。|  
|CBRInputSchema.xsd, CBROutputSchemaCAN.xsd, CBROutputSchemaUS.xsd|分別為輸入格式、加拿大輸出格式和美國輸出格式的結構描述檔案。|  
|CBRPromotedPropertySchema.xsd|對應至已升級屬性的結構描述檔案**CountryCode**項目在 XML 輸入檔。|  
|CBRSample.btproj, CBRSample.sln|此範例的 BizTalk 專案和方案檔。|  
|Cleanup.bat|用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Internet Information Services (IIS) 虛擬目錄。|  
|Setup.bat|用來建置和初始化此範例。|  

## <a name="how-to-use-this-sample"></a>如何使用此範例  
 使用此範例，做為根據內容路由訊息之必要動作的操作範例。  

## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 若要建置和初始化 CBRSample 範例，必須為此範例建置和部署 BizTalk 專案、設定接收埠和位置，以及設定兩個不同的傳送埠。  

#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a>若要為此範例建置和部署 BizTalk 專案  

1. 在命令視窗中，瀏覽至下列資料夾：  

    `<Samples Path>` **\Messaging\CBRSample**  

2. 執行**Setup.bat**，會執行下列動作：  

   - 建立輸入 (**中**) 和輸出資料夾 (**美國**並**可以**) 此範例。  

   - 為這個範例編譯和部署 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  

   - 建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  

   > [!NOTE]
   >  此範例會在建立和繫結連接埠時顯示警告，如下所示：  
   > 
   >  **警告： 接收處理常式，如未指定接收位置"CBRReceiveLocation";更新與第一個接收處理常式，使用符合傳輸類型。**  
   > 
   >  您可以放心地忽略此警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
   > 
   > [!NOTE]
   >  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
   > 
   > [!NOTE]
   >  如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 請使用這個金鑰組來簽署產生的組件。  
   > 
   > [!NOTE]
   >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  

#### <a name="to-prepare-to-configure-the-receive-port-and-location-and-the-send-ports"></a>若要準備設定接收埠和位置以及傳送埠  

1.  在  **Microsoft SQL Management Studio**，選取正確的 BizTalk 管理資料庫。  

    > [!NOTE]
    >  「BizTalk 管理」資料庫也稱為「BizTalk 組態」資料庫。  

#### <a name="to-configure-enlist-and-start-the-us-send-port"></a>若要設定，登錄和啟動美國的傳送埠  

1.  在 BizTalk Server 管理主控台中，依序展開**傳送埠**，以滑鼠右鍵按一下 **[cbrussendport]**，然後按一下**編輯**。  

2.  在 **靜態單向傳送埠屬性**對話方塊的 在資料夾樹狀目錄中，左邊的對話方塊中，選取**篩選 & 對應&#124;篩選**，然後藉由設定新增新的資料列**屬性**要**CBRSample.CountryCode**、 離開**運算子**資料行設為**==**，並設定**值**資料行**100**。  

3.  在對話方塊的左側資料夾樹狀目錄中，選取**篩選 & 對應&#124;輸出對應**，將**要套用的對應**屬性設**CBRSample.CBRInput2USMap**，然後按一下**確定**。 您可能必須按一下捲軸按鈕，才能檢視到對應。  

#### <a name="to-configure-enlist-and-start-the-canadian-send-port"></a>若要設定、登錄和啟動加拿大傳送埠  

1. 在 BizTalk Server 管理主控台中，依序展開**傳送埠**，以滑鼠右鍵按一下 **[cbrcansendport]**，然後按一下**編輯**。  

2. 在 **靜態單向傳送埠屬性**對話方塊的 在資料夾樹狀目錄中，左邊的對話方塊中，選取**篩選 & 對應&#124;篩選**，然後藉由設定新增新的資料列**屬性**要**CBRSample.CountryCode**、 離開**運算子**資料行設為**==**，並設定**值**資料行**200**。  

3. 在對話方塊的左側資料夾樹狀目錄中，選取**篩選 & 對應&#124;輸出對應**，將**要套用的對應**屬性設**CBRSample.CBRInput2CANMap**然後按一下**確定**。  

   這些步驟會將傳送埠連接至接收埠。 範例使用已升級的屬性來路由文件。  

   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 現在已準備就緒可使用此範例。  

## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序執行 CBRSample 範例。  

#### <a name="to-run-this-sample"></a>執行此範例  

1. 將輸入的檔案中，複製 **[cbrdatacan.xml]** 並 **[cbrdataus.xml]**，到下列輸入資料夾：  

    `<Samples Path>` **\Messaging\CBRSample\In**  

2. 觀察每個檔案的轉換方式和路由傳送至下列其中兩個輸出的值為基礎的資料夾及其**CountryCode**項目 (100 和 200):  

   - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 轉換和路由的輸入的檔 **[cbrdatacan.xml]** 資料夾：  

      `<Samples Path>` **\Messaging\CBRSample\CAN**  

   - BizTalk Server 轉換和路由的輸入的檔 **[cbrdataus.xml]** 資料夾：  

      `<Samples Path>` **\Messaging\CBRSample\US**  

## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 無。  

## <a name="see-also"></a>另請參閱  
 [預設管線](../core/default-pipelines.md)   
 [如何設定傳送埠的輸出對應](../core/how-to-configure-outbound-maps-for-a-send-port.md)   
 [傳訊 (BizTalk Server Samples 資料夾)](../core/messaging-biztalk-server-samples-folder.md)