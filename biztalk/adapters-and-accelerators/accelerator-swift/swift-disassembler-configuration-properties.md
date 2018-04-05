---
title: SWIFT 解譯器組態屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disassembler, configuration properties
ms.assetid: 610cc68f-521f-4a9f-9f81-823a2fe55eb1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28bb9cfb95e253eaf6930d14e3856b5fee64deee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler-configuration-properties"></a>SWIFT 解譯器組態屬性
下表提供 SWIFT 解譯器 (DASM) 屬性、 描述、 資料類型和值的範圍。  
  
|屬性名稱|Description|資料類型|數值範圍|  
|-------------------|-----------------|---------------|-----------------|  
|**批次標頭結構描述**|指定您用來剖析批次的信封標頭的一般檔案結構描述。 使用唯有**輸入解除批次處理即將**設**True**。|字串|無或任何已部署的結構描述名稱|  
|**批次結尾結構描述**|指定要用於剖析批次的信封結尾的一般檔案結構描述。 使用唯有**輸入解除批次處理即將**設**True**。|字串|無或任何已部署的結構描述名稱|  
|**BRE 驗證**|啟用/停用的商務規則引擎 (BRE) 驗證引動過程。 如果設定為**True**，訊息會經過驗證，針對已部署的原則 （例如，若要強制執行 SWIFT 網路規則） BRE。 如果設定為**False**，不會叫用 BRE 驗證。|布林|True、False|  
|**雙重類型訊息清單**|指定必須檢查以判斷訊息的子型別動態訊息類型解析期間的第二個標頭欄位的 SWIFT 訊息類型。 預設清單是**102 103 521 523 574**。 **注意：**如果下列任何或所有的訊息類型字串移除雙重類型郵件清單中，則 MT574 以外的所有訊息，原始的結構描述和其商務規則用來處理訊息。 例如，MT102 加上執行個體會使用 MT102、 MT103PLUS 執行個體會使用 MT103、 MT521_ISITC 執行個體會使用 MT521，和 MT523_ISITC 執行個體會使用 MT523。 所有的 MT574 執行個體傳回下列錯誤:"http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/ SWIFT/Category5/MT&#574;SWIFT_CATEGORY5_MT574_Interchange"尋找依訊息類型的文件規格失敗。 確認已正確部署結構描述。 」|字串|3 位數數字的空格分隔的清單|  
|**片段**|啟用/停用的傳入批次的片段。 如果設定為**True**，輸入批次中的訊息會以不同的訊息發行至 MessageBox 資料庫。 如果設定為**False**，整個輸入批次當做單一訊息 （做為輸入的完全相同複本） 發佈到 MessageBox 資料庫。 輸入解除批次處理即將設為時，才使用**True**。|布林|True、False|  
|**輸入解除批次處理即將**|啟用/停用的傳入批次的處理。 如果設定為**True**，應輸入批次，而會分批處理期間。 如果設定為**False**，單一訊息應，而不需要解除批次處理即將。|布林|True、False|  
|**訊息標頭結構描述**|指定要用於剖析訊息信封標頭 （適用於批次中的訊息） 的一般檔案結構描述。 使用唯有**輸入解除批次處理即將**設**True**。|字串|無或任何已部署的結構描述名稱|  
|**訊息結尾結構描述**|指定要用於剖析訊息信封結尾，（用於批次中的訊息） 的一般檔案結構描述。 使用唯有**輸入解除批次處理即將**設**True**。|字串|無或任何已部署的結構描述名稱|  
|**保留批次標頭**|啟用/停用，保留的批次的信封標頭時**片段**已啟用。 如果設定為**True**，批次的信封標頭發佈至 MessageBox 資料庫當做個別訊息。 如果設定為**False**，它會剖析之後，系統會捨棄批次的信封標頭。 使用唯有**批次標頭結構描述**指定。|布林|True、False|  
|**保留批次結尾**|啟用/停用，保留批次的信封的結尾時**片段**已啟用。 如果設定為**True**，批次的信封結尾發佈至 MessageBox 資料庫當做個別訊息。 如果設定為**False**，它會剖析之後，系統會捨棄批次的信封結尾。 使用唯有**批次結尾結構描述**指定。|布林|True、False|  
|**保留訊息標頭**|啟用/停用，保留的訊息信封的標頭 （適用於批次中的訊息） 時**片段**已啟用。 如果設定為**True**，訊息信封標頭發佈至 MessageBox 資料庫中對應的 SWIFT 訊息批次中的標頭部分。 如果設定為**False**，它會剖析之後，系統會捨棄訊息信封標頭。 使用唯有**訊息標頭結構描述**指定。|布林|True、False|  
|**保留訊息結尾**|啟用/停用，保留的訊息信封結尾 （針對批次中的訊息） 時**片段**已啟用。 如果設定為**True**，訊息信封結尾發佈至 MessageBox 資料庫中的批次中的對應 SWIFT 訊息結尾部分。 如果設定為**False**，它會剖析之後，系統會捨棄訊息信封結尾。 使用唯有**訊息結尾結構描述**指定。|布林|True、False|  
|**保留工作階段和序號**|如果設定為**True**，保留標頭區塊 1 中的工作階段和順序編號欄位中的任何字元字串。<br /><br /> 如果設定為**False**，這些欄位中插入已截斷的空格。|布林|True、False|  
|**升級 A4SWIFT SWIFTBound 屬性**|如果設定為**True**，升級**SWIFTBound**透過此管線產生的標頭區塊 2 （輸入） 收到的訊息屬性。<br /><br /> 如果設定為**False**，請勿升級**SWIFTBound**在任何案例中的屬性。|布林|True、False|  
|**隱藏遺漏原則警告**|啟用/停用記錄商務規則引擎 (BRE) 中的警告事件記錄檔遺失 （解除部署） BRE 驗證原則。 如果設定為**True**，會隱藏的警告。 如果設定為**False**，每次找不到驗證原則，就會記錄警告。 使用唯有**BRE 驗證**已啟用。|布林|True、False|  
|**SWIFT 的標頭結構描述**|指定要用於剖析 SWIFT 訊息標頭和檢查的已剖析的值來動態探索訊息類型的一般檔案結構描述。 指定是否需要動態訊息類型解析 （管線會處理不同類型的 SWIFT 訊息）。 如果指定**SWIFT 交換的結構描述**未指定。 如果**SWIFT 交換**和**SWIFT 標頭結構描述**是這兩個未指定， **SWIFT 標頭結構描述**預設為**Micrsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema**。|字串|無或任何已部署的結構描述名稱|  
|**SWIFT 交換的結構描述**|指定要用於剖析整個 SWIFT 訊息 （交換） 的一般檔案結構描述。 指定是否不需要動態訊息類型解析 （管線只會處理指定之型別的 SWIFT 訊息）。 如果必須指定**SWIFT 標頭結構描述**未指定。|字串|無或任何已部署的結構描述名稱|  
|**空白的行視為剖析錯誤**|如果設定為**True**空白行許多的多行欄位中，發生時，這些會標示為剖析的錯誤 （空白行不是根據 SWIFT 很好的作法）。 請注意，如解除批次處理即將案例，這些剖析錯誤不會終止批次處理 （訊息會被視為錯誤的訊息並產生錯誤一部分），而且會正確處理無錯誤批次中的訊息。<br /><br /> 如果設定為**False**，多行的許多欄位中允許使用空白的行。|布林|True、False|  
|**XML 驗證**|啟用/停用的 XML 驗證引動過程。 如果設定為**True**，訊息會經過驗證，驗證讀取器對結構描述條件約束 （例如，若要強制執行的長度或值的範圍） 的 XML。 如果設定為**False**，XML 驗證不會叫用。|布林|True、False|  
  
## <a name="see-also"></a>另請參閱  
 [設定 SWIFT 反組譯工具](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler.md)   
 [設定 SWIFT 組譯工具](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-assembler.md)