---
title: "EDI 解決方案搭配使用的 XML 工具的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d9b361-be98-494c-b32d-03892672fef1
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88edef073bdab21213d9f1f52ec7e4424ff4e4b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-xml-tools-used-with-edi-solutions"></a>與 EDI 解決方案搭配使用之 XML 工具的已知問題
本主題描述 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 中 XML 工具的已知問題。  
  
## <a name="validation-of-test-map-input-and-output-file-still-occurs-when-the-validate-property-is-set-to-false"></a>當 Validate 屬性設定為 False 時，仍然會進行測試對應輸入與輸出檔案的驗證  
 如果您在測試對應 TestMap 輸入屬性設定為**原生**和 驗證 TestMap 輸入 和 驗證 TestMap 輸出屬性設定為**False**，仍然會進行驗證。 因為原生格式的輸入檔案將轉換成 XML 格式，而且 BizTalk Server 將針對結構描述驗證 XML，所以會發生這個問題。 如果輸入檔中有驗證問題，這個驗證機制會公佈錯誤，即使 驗證 TestMap 輸入 和 驗證 TestMap 輸出屬性設定為**False**。  
  
## <a name="length-validation-is-not-performed-on-a-data-element-in-a-generated-instance-that-is-pulled-from-an-enum-list-in-the-schema"></a>系統不會針對提取自結構描述之列舉清單的產生執行個體中的資料元素進行長度驗證  
 當某個執行個體產生自結構描述，而且該結構描述中資料元素的列舉值不符合長度需求時，此執行個體可能會以後續由於長度需求而讓 XSD 驗證失敗的資料元素產生。 結構描述驗證將不會檢查提取自結構描述之列舉清單的產生執行個體中的值是否滿足最小/最大長度需求。  
  
## <a name="validate-schema-may-not-detect-an-invalid-transaction-set-id-code"></a>驗證結構描述可能無法偵測出無效的交易集識別代碼  
 當您驗證結構描述中使用 驗證結構描述命令的 [方案總管] 視窗[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，根節點的檢查可能無法偵測出無效的交易集識別代碼中的根參考節點的最後一個部分 (格式 x12_<\<VersionRelease > 為 X12_&LT;VERSIONRELEASE&GT;_TSID)。 如果結構描述之根參考節點中的 TSID 無效，但是它與結構描述中 ST01 元素之列舉節點的 TSID 相同，[驗證結構描述] 作業將無法偵測出此 TSID 無效。  
  
## <a name="visual-studio-must-be-restarted-to-make-an-enum-change-in-a-schema-effective-for-instance-validation"></a>您必須重新啟動 Visual Studio 才能讓結構描述中的列舉變更針對執行個體驗證生效  
 如果您變更了結構描述中的列舉清單、儲存此結構描述，然後執行執行個體驗證，BizTalk Server 將會根據舊版結構描述而非最新版本進行驗證。 在您重新啟動 Visual Studio 之前，BizTalk Server 將不會使用最新版結構描述。  
  
## <a name="the-edi-instance-properties-dialog-box-may-be-displayed-when-not-needed-in-the-testmap-operation"></a>EDI 執行個體屬性對話方塊可能會在不需要時顯示於 TestMap 作業中  
 BizTalk Server 將會顯示 [EDI 執行個體屬性] 對話方塊兩次在 TestMap 處理期間： 之後，您可以輸入解譯輸入的訊息執行個體和一次輸入分隔符號來產生輸出訊息所需的分隔符號執行個體。 BizTalk Server 應該只會顯示 [EDI 執行個體屬性] 對話方塊兩次，而且僅針對 EDI 結構描述顯示。不過，BizTalk Server 可能會針對非 EDI 結構描述顯示此對話方塊，而且不僅顯示兩次。 如果發生這個問題，請關閉此對話方塊。  
  
## <a name="validation-of-an-xml-preserved-interchange-is-not-supported"></a>不支援 XML 保留交換的驗證  
 當驗證保留的交換，如果您選取 XML for**驗證執行個體輸入類型**屬性，則作業會失敗並不會傳回。 不過，如果您選取**原生**如**驗證執行個體輸入類型**時驗證保留的交換，則作業會成功。  
  
## <a name="an-instance-generated-for-a-hipaa-278-schema-will-contain-both-request-and-response-sections"></a>針對 HIPAA 278 結構描述產生的執行個體將同時包含要求與回應區段  
 HIPAA 278 結構描述會同時用於 278 要求和 278 回應訊息。 如果您針對 278 結構描述使用 [產生執行個體] 命令，產生的執行個體將同時含有要求與回應區段，而系統應該永遠都不會傳送這兩個區段。 若要建立可用的 278 要求或 278 回應訊息，請在文字編輯器中開啟 XML 工具所產生的執行個體，然後刪除其中一個區段，例如刪除要求訊息的回應區段。  
  
 如果您針對同時含有要求與回應區段的 278 訊息執行 [驗證執行個體] 命令，此訊息將成功地針對 278 結構描述進行驗證。  
  
## <a name="an-xml-instance-generated-from-a-278-hipaa-schema-will-fail-validation"></a>產生自 278 HIPAA 結構描述的 XML 執行個體將會讓驗證失敗  
 如果您使用「執行個體產生」命令，從 278 HIPAA 結構描述中產生 XML 執行個體，然後使用「執行個體驗證」命令來驗證該執行個體，BizTalk Server 將會公佈錯誤。  
  
## <a name="a-native-instance-generated-from-a-837-schema-incorrectly-sets-gs08"></a>從 837 結構描述產生的原生執行個體不正確地設定 GS08  
 產生原生執行個體使用時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含 X12_BatchSchema 和 837I、 837d 或 837p 結構描述的 GS08 值的方案將會包含 00401。 再處理這個執行個體，您必須為正確的結構描述執行個體的值變更 GS08 的值。  下表包含每個 837 結構描述的正確 GS08 值：  
  
|HIPAA 結構描述|GS08 值|  
|------------------|----------------|  
|837I|004010X096A1|  
|837D|004010X097A1|  
|837P|004010X098A1|  
  
## <a name="see-also"></a>另請參閱  
 [EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md)   
 [使用 XML 工具延伸模組](../core/using-the-xml-tool-extensions.md)   
 [使用設計階段 XML 工具](../core/using-design-time-xml-tools.md)