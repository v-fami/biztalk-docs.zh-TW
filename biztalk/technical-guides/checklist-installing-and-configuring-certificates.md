---
title: 檢查清單： 安裝及設定憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76a8f8f6-8d79-4caf-8fba-8cbcb251d461
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e675a60967b5ee34c40f1711f256aff76362d2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300494"
---
# <a name="checklist-installing-and-configuring-certificates"></a>檢查清單： 安裝及設定憑證
本主題說明設定 BizTalk Server 搭配使用的憑證所需的步驟。  
  
|步驟|參考|  
|-----------|---------------|  
|評估您的憑證需求，並於協議與交易夥伴有關憑證與您相互的責任。|「 評估和憑證的使用規劃 > 一節中[管理憑證的最佳作法](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|如果您將會使用私密金鑰，憑證授權單位 (CA) 要求數位簽章的私密-公開金鑰組，並將公開金鑰傳送給交易夥伴。<br /><br /> 如果您將使用的公開金鑰，有交易夥伴要求來自 CA 的數位簽章的私密-公開金鑰組，並將公開金鑰傳送給您。|[如何安裝 BizTalk Server 的憑證](~/technical-guides/how-to-install-certificates-for-biztalk-server.md)|  
|安裝私人或公用金鑰至適當的憑證存放區中，而且有執行相同的交易夥伴。|-   [如何安裝 BizTalk Server 的憑證](~/technical-guides/how-to-install-certificates-for-biztalk-server.md)<br />-[安裝憑證] 區段[管理憑證的最佳作法](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|如果 MIME/SMIME 訊息中使用的憑證，設定 BizTalk Server 使用的憑證。|-   [設定 MIME 或 SMIME 訊息的憑證](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)<br />-中的 」 設定 BizTalk Server 來使用憑證來 MIME/SMIME 」 一節[管理憑證的最佳作法](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|（選擇性）如果與配接器使用的憑證，設定配接器使用的憑證。|-   [設定與介面卡的憑證](~/technical-guides/configuring-certificates-with-adapters.md)<br />-< 設定 BizTalk 配接器使用的憑證 > 一節[管理憑證的最佳作法](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|（選擇性）如果使用的憑證來執行合作對象解析，設定為使用憑證的合作對象。|[如何設定合作對象解析的憑證](~/technical-guides/how-to-configure-certificates-for-party-resolution.md)|  
|（選擇性）如果將憑證從一個 BizTalk 群組匯出到另一個，將憑證新增至 BizTalk 應用程式中，匯出至.msi 檔案; 應用程式然後再將應用程式匯入不同的 BizTalk 群組。|-   [如何設定合作對象解析的憑證](~/technical-guides/how-to-configure-certificates-for-party-resolution.md)<br />-   [如何匯出至.msi 檔案的應用程式](~/technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   [如何從.msi 檔案匯入應用程式](~/technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-「 匯出憑證從一個 BizTalk 群組到另一個 > 一節的[管理憑證的最佳作法](~/technical-guides/best-practices-for-managing-certificates2.md)|  
  
## <a name="see-also"></a>另請參閱  
 [管理憑證的最佳作法](~/technical-guides/best-practices-for-managing-certificates2.md)   
 [在 BizTalk Server 中憑證的已知的問題](~/technical-guides/known-issues-with-certificates-in-biztalk-server.md)