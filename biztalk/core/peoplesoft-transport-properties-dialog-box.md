---
title: PeopleSoft 傳輸屬性對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PeopleSoft
helpviewer_keywords:
- PeopleSoft Transport Properties dialog box
ms.assetid: 660f0a0b-e076-4f4e-8b2a-6d976acfc5ce
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50362e60b982a2d304efea8c26f58019148e5c16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="peoplesoft-transport-properties-dialog-box"></a>PeopleSoft 傳輸屬性對話方塊
使用 [PeopleSoft Transport 傳輸屬性] 對話方塊設定配接器必要屬性。  
  
|使用|動作|  
|--------------|----------------|  
|**配接器必要屬性**||  
|應用程式伺服器路徑|輸入 PeopleSoft server 的路徑 (例如， `//psserver.domain.com:9000`)。|  
|JAVA_HOME|輸入 JAVA_HOME 位置的名稱 (例如， `<drive:>\jdk1.4.2_08`)。|  
|密碼|輸入這個使用者的密碼。|  
|PeopleSoft 8.x JAR 檔案|輸入 PeopleSoft JAR 檔案的位置路徑 (例如， `<drive:>\JAR_FILES\Peoplesoft_8.4\psjoa.jar`)。|  
|使用者名稱|輸入使用者名稱，然後按一下**確定**。|  
|**其他參數**||  
|資料庫日期格式|輸入您想要出現日期的格式 (例如，**YYYY MM DD**)。<br /><br /> 當日期做為索引鍵使用時，格式將不同。|  
|**並行控制**||  
|同時呼叫數目上限|輸入的數值**同時呼叫數目上限**。 此數目代表同時呼叫的數目上限，例如 200。<br /><br /> 此欄位 的預設值為 -1，表示不會提供保護 。|  
|**連接**||  
|工作階段數目上限|輸入代表工作階段數目上限的數目。<br /><br /> 預設的連線次數為 40。|  
|**重新整理代理程式**||  
|重新整理代理程式|選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。<br /><br /> 例如，您希望程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在配接器精靈的選項中。|  
|**單一登入**||  
|分支機構應用程式|只有在您使用單一登入 (SSO) 時，才需從清單中選取分支機構應用程式。|  
|使用 SSO|選取**是**如果您使用 SSO; 密碼就不需要在此情況下。 **注意：**如果您已輸入密碼，而且您想要使用單一登入，以滑鼠右鍵按一下欄位和選取的密碼**將密碼**。|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for PeopleSoft Enterprise 的 UI 參考](../core/ui-reference-for-biztalk-adapter-for-peoplesoft-enterprise.md)