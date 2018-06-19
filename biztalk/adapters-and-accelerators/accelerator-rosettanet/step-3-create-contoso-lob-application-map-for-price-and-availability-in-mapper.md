---
title: 步驟 3： 建立 Contoso LOB 應用程式會將對應為價格與可用性專案使用的 BizTalk 對應工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOB maps
ms.assetid: a947e0ac-f0cb-4be9-85a8-09daf3675b1a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fef0f6e951798dd2453aa387d8dcde9853968f3a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964988"
---
# <a name="step-3-creating-the-contoso-lob-application-maps-for-the-price-and-availability-project-using-biztalk-mapper"></a>步驟 3： 建立 Contoso LOB 應用程式對應的價格與可用性專案使用 BizTalk 對應工具
在此步驟中，您將建立兩種對應，用以定義兩個交易夥伴之間成功交換訊息所需的轉換。 就本實例而言，Contoso ERP 系統已經標準化「價格與可用性」要求的訊息格式。 這兩種對應會在交易夥伴 Fabrikam 傳來的要求及回應訊息與內部定義的 Contoso 訊息之間建立對應關係。  
  
### <a name="to-add-a-reference-for-the-3a2-priceandavailability-request-schema"></a>為 3A2 PriceAndAvailability 要求結構描述加入參考  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [contosopriceandavailability] 專案，然後**加入參考**。  
  
2.  在 [加入參考] 對話方塊中，按一下**瀏覽**。  
  
3.  移至資料夾*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\Bin，然後選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**組件。  
  
4.  按一下**新增**，然後按一下 **確定**。  
  
### <a name="to-create-the-3a2-priceandavailability-request-to-contoso-priceandavailability-request-map"></a>建立從 3A2 PriceAndAvailability 要求到 Contoso PriceAndAvailability 要求的對應  
  
1.  在 方案總管 中，以滑鼠右鍵按一下 contosopriceandavailability 專案，指向**新增**，然後按一下 **新項目**。  
  
2.  在 加入新項目-ContosoPriceAndAvailability 對話方塊中，選取 **對應檔**在分類窗格中，然後選取**對應**中**範本**窗格。 在**名稱**方塊中，輸入**PIP3A2RequestToContosoPriceRequest**，然後按一下 **新增**。  
  
### <a name="to-associate-the-schemas-for-the-pip3a2requesttocontosopricerequest-map"></a>產生 PIP3A2RequestToContosoPriceRequest 對應的結構描述關聯  
  
1.  (已顯示 pip3a2requesttocontosopricerequest.btm)，BizTalk 對應工具中的來源結構描述窗格中，按一下 **開啟來源結構描述**。  
  
2.  在 [BizTalk 型別選擇器] 對話方塊中，依序展開**ContosoPriceAndAvailability**，依序展開**參考**，依序展開**Microsoft.Solutions.BTARN.Schemas.RNPIPs**，然後展開**結構描述。**  
  
3.  選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs。**  
  
     **_3a2priceandavailabilityquerymessageguideline_v1_3]**，然後按一下 [**確定**。  
  
4.  在 [目的結構描述] 窗格中，按一下**開啟目的結構描述**。  
  
5.  在 [BizTalk 型別選擇器] 對話方塊中，依序展開**ContosoPriceAndAvailability**，然後展開**結構描述**。  
  
6.  選取**ContosoPriceAndAvailability.ContosoPriceSchema**結構描述，然後再按一下**確定**。  
  
7.  在根節點目標結構描述 對話方塊中，選取**rootPriceRequest**結構描述，然後再按一下**確定**。  
  
### <a name="to-link-schema-fields-in-the-pip3a2requesttocontosopricerequest-map"></a>連結 PIP3A2RequestToContosoPriceRequest 對應中的結構描述欄位  
  
1.  在目的結構描述窗格中，以滑鼠右鍵按一下**\<結構描述\>** 節點，然後再按一下**展開樹狀結構節點**。  
  
2.  在來源結構描述窗格中，以滑鼠右鍵按一下**\<結構描述\>** 節點，然後再按一下**展開樹狀結構節點**。  
  
3.  拖曳**GlobalProductIdentifier**欄位設為**ProductID**在目的結構描述 窗格中的欄位。  
  
    > [!NOTE]
    >  您可以找到**GlobalProductIdentifier**欄位中的節點 Pip3A2PriceAndAvailabilityQuery/ProductPriceAndAvailabilityQuery /  
    >   
    >  欄位  
    >   
    >  。  
  
4.  在**檔案**功能表上，按一下 **全部儲存**以儲存變更。  
  
## <a name="see-also"></a>請參閱  
 [建立與設定 BizTalk 連接埠以供 Contoso 使用](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)