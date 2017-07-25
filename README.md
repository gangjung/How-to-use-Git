# Git ���� ����ϴ� ��ɾ� ����
���� ����ϴ� �⺻���� ��ɾ���� �����߽��ϴ�.

-- �ֱ� ������ : 2017-07-25

## ����� ����(�ʱ�ȭ) �ϱ�
```bash
git init    # ����� ����
```

## Ŀ���ϱ�
```bash
git add README.md    # Ŀ���� ���� �߰�
git status    # ���� stage ���¸� Ȯ��
git commit -m "init:README.md"    # �ζ��� Ŀ�� �޽��� �ۼ�
git log --deccorate=full --online --graph    # Ŀ�� �α� Ȯ��
```

## �귣ġ �����ϱ�
```bash
git checkout -b readme    # readme ��� �̸��� �귣ġ�� ������ ��, ������ �귣ġ�� üũ�ƿ�
```

## �����ϱ�
```bash
git merge readme --no-ff # readme �귣ġ�� ������ �ڰܿͼ� ������, fast-forword��� ��
```

# LICENSE
�� ����Ҵ� WTFPL ���̼����� ���� ��ȣ�� �޽��ϴ�.
# ���

PR ���� ��