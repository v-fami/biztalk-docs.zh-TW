---
title: "取代公開金鑰 Token 公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Replace Public Key Token Utility
- utilities, Replace Public Key Token Utility
- public key token
ms.assetid: ed8673b9-af06-4bd7-b8b7-7371e4dd0fed
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 344b25b83060143b339a6791ecae6f3ab7028055
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="replace-public-key-token-utility"></a>取代公開金鑰 Token 公用程式
這個公用程式可使用衍生自強式名稱組件金鑰 (.snk) 檔案的公開金鑰 Token 來取代檔案中的公開金鑰 Token 或變數。  
  
 當開發人員在撰寫的指令碼使用此公用程式可能會很有用[BTSTask 命令列參考](../core/btstask-command-line-reference.md)部署組件。 部署若要成功，就必須提供組件的完整格式名稱，其中會包含其公開金鑰 Token。 組件的公開金鑰 Token 是擷取自 .snk 檔案，並且會在建立時指派給組件。 不過，組件在部署到新環境之前，常使用不同的公開金鑰 Token 重新建置。 因此，開發人員可能不知道在部署指令碼執行時，會為組件使用哪一個公開金鑰 Token。  
  
 您可透過兩種方式來使用「取代公開金鑰 Token」公用程式解決這種狀況：  
  
-   **案例 1。** 在部署指令碼中，開發人員可以使用公開金鑰 Token 或代表公開金鑰 Token 的預留位置。 在執行指令碼之前，使用者可以執行「取代公開金鑰 Token」公用程式，以擷取自 .snk 檔案的公開金鑰 Token 來取代指令碼檔案中的公開金鑰 Token 或預留位置 (.snk 檔案是用來建置目的環境的組件)。  
  
-   **案例 2。** 開發人員可以設定為自動，如下所示取代新的公開金鑰 token，指令碼： 在指令碼開始時，叫用 「 取代公開金鑰 Token 」 公用程式，並指向包含公開金鑰 token 的.snk 檔案。 在指令碼內使用環境變數 %NEWTOKEN% 來代表公開金鑰 Token。 當指令碼執行時，公用程式會從 .snk 檔案擷取公開金鑰 Token 的值，並將其設定為環境變數 %NEWTOKEN%。 當指令碼執行時，每個 %NEWTOKEN% 執行個體都會取代為指定 .snk 檔案的公開金鑰 Token。 例如：  
  
    ```  
    ReplacePKT.bat key.snk  
    ...  
    ...  
    gacutil /u Assembly, ... PublicKey=%NEWTOKEN% ...  
    ```  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 「取代公開金鑰 Token」公用程式位於：  
  
 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\ReplacePublicKeyToken\\。  
  
 「取代公開金鑰 Token」公用程式是由三個檔案所組成：  
  
-   ReplacePKT.bat  
  
-   ReplacePKT.vbs  
  
-   ReplacePKT.wsf  
  
## <a name="procedures"></a>程序  
 請使用下列程序，利用擷取自 .snk 檔案的公開金鑰 Token，取代檔案中公開金鑰 Token 或預留位置的所有執行個體。  
  
#### <a name="to-replace-instances-of-a-public-key-token-or-a-placeholder-in-a-file"></a>取代檔案中公開金鑰 Token 或預留位置的執行個體  
  
1.  確定三個「取代公開金鑰 Token」公用程式檔案 (ReplacePKT.bat、ReplacePKT.vbs、ReplacePKT.wsf)、指令碼檔案和 .snk 檔案都可以從本機電腦使用。  
  
2.  在命令視窗中，將目錄變更為包含「取代公開金鑰 Token」公用程式檔案。  
  
3.  從命令提示字元中執行下列命令：  
  
4.  **ReplacePKT \<**  *.snk 檔案*  **\> \<**  *舊公開金鑰語彙基元*  **\> \<**  *檔案取代***\>**  
  
    |選項|Description|  
    |------------|-----------------|  
    |**\<***.snk 檔案***\>**|.snk 檔案的完整路徑，此檔案所包含的公開金鑰 Token 會用來取代現有的公開金鑰 Token 或預留位置。|  
    |**\<***舊公開金鑰語彙基元***\>**|要取代的公開金鑰 Token 或預留位置。|  
    |**\<***檔案取代***\>**|檔案的完整路徑，您要取代此檔案中的公開金鑰 Token 或預留位置。|  
  
     範例：  
  
     **ReplacePKT.bat C:\Tokens\MyToken.snk 12ab3456cd789e12 C:\Scripts\MyScript.vbs**  
  
 請使用下列程序自動在指令碼中設定環境變數，以使用衍生自 .snk 檔案的公開金鑰 Token，如案例 2 所述。  
  
#### <a name="to-set-an-environment-variable-that-uses-a-public-key-token"></a>設定使用公開金鑰 Token 的環境變數  
  
1.  在指令碼檔案開頭加入以下的程式碼行：  
  
    ```  
    ReplacePKT <filename>.snk  
    ```  
  
     其中\< *filename* \>是要從中衍生的公開金鑰 token 的.snk 檔案的名稱。  
  
    ```  
    Example: ReplacePKT.bat MyToken.snk  
    ```  
  
2.  在指令碼檔案中，使用 `%NEWTOKEN%` 來代表公開金鑰 Token。  
  
     範例：  
  
    ```  
    PublicKey=%NEWTOKEN%  
    ```  
  
3.  將指令碼檔案提供給使用者時，請包含構成「取代公開金鑰 Token」公用程式的三個檔案 (ReplacePKT.bat、ReplacePKT.vbs、ReplacePKT.wsf)。 請確定指令碼使用者先將所有這些檔案複製到檔案系統上的相同資料夾中，然後再執行指令碼。  
  
## <a name="see-also"></a>請參閱  
 [SDK 中的公用程式](../core/utilities-in-the-sdk.md)