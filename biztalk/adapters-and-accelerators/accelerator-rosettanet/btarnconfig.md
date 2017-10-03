---
title: "BtarnConfig |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, exporting configuration data
- BTARN, BtarnConfig utility
- BtarnConfig utility
- BTARN, importing configuration data
ms.assetid: 8c95be2a-7df5-47fb-ae2d-64fa27e2811a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9221e530266091795260bc7d4fd7e8788e066335
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="btarnconfig"></a>BtarnConfig
您可使用 BtarnConfig 公用程式將組態資料匯入 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 環境，或是從此環境匯出組態資料。 組態資料便是使用 BTARN 管理主控台設定的資料，其中包括有程序組態設定、主要組織、夥伴和協議。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK  
  
## <a name="running-btarnconfig"></a>執行 BtarnConfig  
  
#### <a name="to-run-btarnconfig"></a>若要執行 BtarnConfig  
  
1.  開啟命令提示字元。  
  
2.  移至\<*磁碟機*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\\。  
  
3.  在命令提示字元中，輸入**BtarnConfig**，輸入適當的參數，然後按 ENTER 鍵。  
  
    > [!NOTE]
    >  下節會說明這些參數。  
  
## <a name="syntax-for-btarnconfig"></a>BtarnConfig 的語法  
 以下是用來啟動這個命令列工具的語法：  
  
### <a name="syntax-for-importing-configuration-data"></a>用來匯入組態資料的語法  
  
```  
BTARNCONFIG /IMPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  
  
### <a name="syntax-for-exporting-configuration-data"></a>用來匯出組態資料的語法  
  
```  
BTARNCONFIG /EXPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  
  
### <a name="syntax-description"></a>語法描述  
 下表說明 BtarnConfig 公用程式所使用語法的每個部分。  
  
|語法|Description|  
|------------|-----------------|  
|\<*檔名*.xml >|匯入或匯出檔案的來源或目的地的完整路徑。 如果您未提供路徑，BTARN 會假設路徑\<*磁碟機*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK。|  
|**/ 匯入**|匯入 XML 資料從\< *filename*.xml > 入 BTARN 組態。|  
|**/ 匯出**|將 BTARN 組態匯出為 XML 資料轉換成\< *filename*.xml >。|  
|**/H**|匯入或匯出主要組織的組態資料。|  
|**/ P**|匯入或匯出交易夥伴的組態資料。|  
|**/R**|匯入或匯出程序的組態資料。|  
|**/ A**|匯入或匯出協議的組態資料。|  
  
## <a name="remarks"></a>備註  
 如果您未提供任何一個**/H**， **/P**， **/R**，或**/A**參數的 BtarnConfig 公用程式匯入或匯出的所有資料。 在一次作業中就匯出所有的資料時，BtarnConfig 會依照下列順序，將這些資料匯出為 XML 檔案：主要組織、交易夥伴、程序組態和協議。  
  
 如果您正要進行匯入作業的來源檔案中，存在結構性的問題，BTARN 將會在結構描述驗證階段期間，偵測到錯誤。因此在資料尚未匯入之前，作業就會失敗。 如果發生其他錯誤，例如您正在嘗試匯入複製的成品或是 PIP/協議需要 HTTPS，則匯入作業也會失敗。 然而，所有已匯入該位置的資料將會持續保留在組態中。  
  
 您必須是 BizTalk 系統管理員，才能使用 BtarnConfig 進行組態資料的匯入或匯出作業。 如果您不是 BizTalk 系統管理員，某些匯入作業會因為存取權限的問題而失敗。 但是，其他以相同 BtarnConfig 命令進行的匯入作業則有可能會成功。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)